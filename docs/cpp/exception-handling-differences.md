---
title: "Diferencias en el control de excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++, frente a control estructurado de excepciones"
  - "excepciones, clase contenedora"
  - "control estructurado de excepciones, frente a control de excepciones de C++"
  - "control estructurado de excepciones, no estructurado"
  - "clases contenedoras, excepción de C"
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Diferencias en el control de excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La diferencia principal entre el control de excepciones estructurado y el control de excepciones de C\+\+ consiste en que el modelo de control de excepciones de C\+\+ trata los tipos, mientras que el modelo de control de excepciones estructurado de C trata las excepciones de un tipo, específicamente, `unsigned int`.  Es decir, las excepciones de C se identifican mediante un valor entero sin signo, mientras que las excepciones de C\+\+ se identifican mediante el tipo de datos.  Cuando se produce una excepción en C, cada controlador posible ejecuta un filtro que examina el contexto de excepción de C y determina si debe aceptar la excepción, pasarla a otro controlador u omitirla.  Cuando se produce una excepción en C\+\+, puede ser de cualquier tipo.  
  
 Una segunda diferencia se debe a que el modelo de control de excepciones estructurado de C se denomina "asincrónico" porque las excepciones se producen de forma secundaria al flujo de control normal.  El mecanismo de control de excepciones de C\+\+ es totalmente "sincrónico", lo que significa que las excepciones aparecen solo cuando se producen.  
  
 Si se produce una excepción de C en un programa de C\+\+, puede administrarse mediante un controlador de excepciones estructurado con su filtro asociado o mediante un controlador **catch** de C\+\+, lo que sea dinámicamente más próximo al contexto de la excepción.  Por ejemplo, el siguiente programa de C\+\+ provoca una excepción de C en el contexto **try** de C\+\+:  
  
## Ejemplo  
  
```  
// exceptions_Exception_Handling_Differences.cpp  
// compile with: /EHa  
#include <iostream>  
  
using namespace std;  
void SEHFunc( void );  
  
int main() {  
   try {  
      SEHFunc();  
   }  
   catch( ... ) {  
      cout << "Caught a C exception."<< endl;  
   }  
}  
  
void SEHFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
   }  
   __finally {  
      cout << "In finally." << endl;  
   }  
}  
```  
  
  **En finally.**  
**Se detectó una excepción de C.**   
##  <a name="_core_c_exception_wrapper_class"></a> Clase contenedora de excepciones de C  
 En un ejemplo sencillo como el anterior, la excepción de C solamente se puede detectar con un controlador **catch** de puntos suspensivos \(**...**\).  No se comunica al controlador ninguna información sobre el tipo o la naturaleza de la excepción.  Aunque este método funcione, en algunos casos puede ser necesario definir una transformación entre los dos modelos de control de excepciones para asociar cada excepción de C a una clase concreta.  Para ello, se puede definir una clase "contenedora" de excepciones de C, que se puede utilizar o de la que se puede derivar para atribuir un tipo de clase concreto a una excepción de C.  Al hacerlo, cada excepción de C se puede controlar mediante un controlador **catch** de C\+\+ de forma más independiente que en el ejemplo anterior.  
  
 La clase contenedora puede tener una interfaz que se compone de algunas funciones miembro que determinan el valor de la excepción y que tienen acceso a la información extendida del contexto de la excepción proporcionada por el modelo de excepciones de C.  Puede que también desee definir un constructor predeterminado y un constructor que acepte un argumento `unsigned int` \(para proporcionar la representación subyacente de la excepción de C\) y un constructor de copias bit a bit.  A continuación se muestra una posible implementación de la clase contenedora de excepciones de C:  
  
```  
// exceptions_Exception_Handling_Differences2.cpp  
// compile with: /c  
class SE_Exception {  
private:  
   SE_Exception() {}  
   SE_Exception( SE_Exception& ) {}  
   unsigned int nSE;  
public:  
   SE_Exception( unsigned int n ) : nSE( n ) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() {  
      return nSE;  
   }  
};  
  
```  
  
 Para utilizar esta clase, se debe instalar una función personalizada de traducción de excepciones de C a la que llama el mecanismo de control de excepciones internas cada vez que se produce una excepción de C.  Dentro de la función de traducción, puede producirse cualquier excepción con tipo \(quizás un tipo `SE_Exception` o un tipo de clase derivada de `SE_Exception`\) que se puede detectar mediante un controlador coincidente adecuado **catch** de C\+\+.  La función de traducción simplemente puede volver, lo que indica que no controló la excepción.  Si la propia función de traducción provoca una excepción de C, se llama a [terminate](../c-runtime-library/reference/terminate-crt.md).  
  
 Para especificar una función de traducción personalizada, llame a la función [\_set\_se\_translator](../c-runtime-library/reference/set-se-translator.md) con el nombre de la función de traducción como su único argumento.  La función de traducción que escriba se llama una vez para cada invocación de función en la pila que tenga bloques **try**.  No hay ninguna función de traducción predeterminada; si no se especifica una mediante una llamada a `_set_se_translator`, la excepción de C solo se puede capturar con un controlador **catch** de puntos suspensivos.  
  
## Ejemplo  
 Por ejemplo, el código siguiente instala una función de traducción personalizada y, a continuación, provoca una excepción de C que se ajusta mediante la clase `SE_Exception`:  
  
```  
// exceptions_Exception_Handling_Differences3.cpp  
// compile with: /EHa  
#include <stdio.h>  
#include <eh.h>  
#include <windows.h>  
  
class SE_Exception {  
private:  
   SE_Exception() {}  
   unsigned int nSE;  
  
public:  
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}  
   SE_Exception(unsigned int n) : nSE(n) {}  
   ~SE_Exception() {}  
   unsigned int getSeNumber() { return nSE; }  
};  
  
void SEFunc() {  
   __try {  
      int x, y = 0;  
      x = 5 / y;  
    }  
    __finally {  
      printf_s( "In finally\n" );  
   }  
}  
  
void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {  
   printf_s( "In trans_func.\n" );  
   throw SE_Exception( u );  
}  
  
int main() {  
   _set_se_translator( trans_func );  
    try {  
      SEFunc();  
    }  
    catch( SE_Exception e ) {  
      printf_s( "Caught a __try exception with SE_Exception.\n" );  
      printf_s( "nSE = 0x%x\n", e.getSeNumber() );  
    }  
}  
```  
  
  **En trans\_func.**  
**En finally.**  
**Se detectó una excepción \_\_try con SE\_Exception.**  
**nSE \= 0xc0000094**   
## Vea también  
 [Mezclar excepciones de C \(Estructurado\) y C\+\+](../cpp/mixing-c-structured-and-cpp-exceptions.md)