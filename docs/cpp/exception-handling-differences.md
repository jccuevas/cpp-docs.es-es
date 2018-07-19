---
title: Diferencias de control de excepciones | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dafb3c41bd490e7c123e1aefe9ccaa04a4e6b233
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944522"
---
# <a name="exception-handling-differences"></a>Diferencias en el control de excepciones
La principal diferencia entre el control estructurado de excepciones y control de excepciones de C++ es que el modelo trata los tipos de control de excepciones de C++, mientras el C modelo de control de excepciones estructurado trata las excepciones de un tipo, en concreto,  **int sin signo**. Es decir, las excepciones de C se identifican mediante un valor entero sin signo, mientras que las excepciones de C++ se identifican mediante el tipo de datos. Cuando se produce una excepción en C, cada controlador posible ejecuta un filtro que examina el contexto de excepción de C y determina si debe aceptar la excepción, pasarla a otro controlador u omitirla. Cuando se produce una excepción en C++, puede ser de cualquier tipo.  
  
 Una segunda diferencia se debe a que el modelo de control de excepciones estructurado de C se denomina "asincrónico" porque las excepciones se producen de forma secundaria al flujo de control normal. El mecanismo de control de excepciones de C++ es totalmente "sincrónico", lo que significa que las excepciones aparecen solo cuando se producen.  
  
 Si se produce una excepción de C en un programa de C++, puede controlarse mediante un controlador de excepciones estructurado con su filtro asociado o C++ **catch** controlador, lo que sea dinámicamente más próximo del contexto de la excepción. Por ejemplo, el programa C++ siguiente genera una excepción de C, c++ **intente** contexto:  
  
## <a name="example"></a>Ejemplo  
  
```cpp 
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
  
```Output  
In finally.  
Caught a C exception.  
```  
  
##  <a name="_core_c_exception_wrapper_class"></a> Clase contenedora de excepciones de C  
 En un ejemplo sencillo como el anterior, se puede detectar la excepción de C solo por puntos suspensivos (**...** ) **catch** controlador. No se comunica al controlador ninguna información sobre el tipo o la naturaleza de la excepción. Aunque este método funcione, en algunos casos puede ser necesario definir una transformación entre los dos modelos de control de excepciones para asociar cada excepción de C a una clase concreta. Para ello, se puede definir una clase "contenedora" de excepciones de C, que se puede utilizar o de la que se puede derivar para atribuir un tipo de clase concreto a una excepción de C. Al hacerlo, cada excepción de C puede controlarse mediante C++ **catch** controlador más por separado que en el ejemplo anterior.  
  
 La clase contenedora puede tener una interfaz que se compone de algunas funciones miembro que determinan el valor de la excepción y que tienen acceso a la información extendida del contexto de la excepción proporcionada por el modelo de excepciones de C. También puede definir un constructor predeterminado y un constructor que acepta un **int sin signo** argumento (para proporcionar para la representación de excepción subyacente de C) y un constructor de copias bit a bit. A continuación se muestra una posible implementación de la clase contenedora de excepciones de C:  
  
```cpp 
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
  
 Para utilizar esta clase, se debe instalar una función personalizada de traducción de excepciones de C a la que llama el mecanismo de control de excepciones internas cada vez que se produce una excepción de C. Dentro de la función de traducción, se puede producir cualquier excepción con tipo (quizás un `SE_Exception` tipo o un tipo de clase derivada de `SE_Exception`) que se puede detectar mediante un C++ coincidente adecuado **catch** controlador. La función de traducción simplemente puede volver, lo que indica que no controló la excepción. Si la propia función de traducción provoca una excepción de C, [finalizar](../c-runtime-library/reference/terminate-crt.md) se llama.  
  
 Para especificar una función de traducción personalizada, llame a la [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) función con el nombre de la función de traducción como su único argumento. La función de traducción que escriba se llama una vez para cada invocación de función en la pila que tenga **intente** bloques. No hay ninguna función de traducción predeterminada; Si no especifica una mediante una llamada a `_set_se_translator`, solo se puede detectar la excepción de C mediante puntos suspensivos **catch** controlador.  
  
## <a name="example"></a>Ejemplo  
 Por ejemplo, el código siguiente instala una función de traducción personalizada y, a continuación, provoca una excepción de C que se ajusta mediante la clase `SE_Exception`:  
  
```cpp 
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
  
```Output  
In trans_func.  
In finally  
Caught a __try exception with SE_Exception.  
nSE = 0xc0000094  
```  
  
## <a name="see-also"></a>Vea también  
 [Mezclar excepciones de C (estructuradas) y de C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)