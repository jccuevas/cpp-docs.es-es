---
title: "Conceptos b&#225;sicos del uso de excepciones administradas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__finally (palabra clave), excepciones administradas"
  - "bloques catch"
  - "excepciones, administradas"
  - "producir excepciones, excepciones administradas"
  - "control de excepciones try-catch"
  - "control de excepciones try-catch, aplicaciones administradas"
  - "Visual C++, controlar excepciones administradas"
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conceptos b&#225;sicos del uso de excepciones administradas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema trata el control de excepciones en las aplicaciones administradas.  Es decir, una aplicación que se compila con la opción del compilador **\/clr** .  
  
## En este tema  
  
-   [Excepciones en \/clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [Bloques try\/catch para extensiones de CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## Comentarios  
 Si compila con la opción de **\/clr** , puede controlar las excepciones así como [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md) estándar y [control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md) \(SEH\).  Una excepción de CLR es cualquier excepción producida por un tipo administrado.  La clase de [System::Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx) proporciona numerosos métodos útiles para procesar las excepciones de CLR y se recomienda como clase base para las clases de excepción definida por el usuario.  
  
 La detección de los tipos de excepción derivados de una interfaz no se admite en **\/clr**.  También, Common Language Runtime no permite que se detecte excepciones de desbordamiento de pila; una excepción de desbordamiento de pila finalizará el proceso.  
  
 Para obtener más información sobre las diferencias en el control de excepciones en código administrado y aplicaciones no administradas, vea [Diferencias de Exception que administra las Extensiones administradas para C\+\+ de Under de comportamiento](../dotnet/differences-in-exception-handling-behavior-under-clr.md).  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> Excepciones en \/clr  
 La expresión throw de C\+\+ se extiende para producir un identificador a un tipo CLR.  El ejemplo siguiente crea un tipo de excepción personalizado y inicia una instancia de ese tipo:  
  
```  
// clr_exception_handling.cpp  
// compile with: /clr /c  
ref struct MyStruct: public System::Exception {  
public:  
   int i;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   throw pMyStruct;  
}  
```  
  
 Un tipo de valor debe aplicar antes de iniciar:  
  
```  
// clr_exception_handling_2.cpp  
// compile with: /clr /c  
value struct MyValueStruct {  
   int i;  
};  
  
void GlobalFunction() {  
   MyValueStruct v = {11};  
   throw (MyValueStruct ^)v;  
}  
```  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> Bloques try\/catch para extensiones de CLR  
 Mismo **try**y estructura de bloque de**catch** se puede utilizar para detectar CLR y excepciones nativas:  
  
```  
// clr_exception_handling_3.cpp  
// compile with: /clr  
using namespace System;  
ref struct MyStruct : public Exception {  
public:  
   int i;  
};  
  
struct CMyClass {  
public:  
   double d;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   pMyStruct->i = 11;  
   throw pMyStruct;  
}  
  
void GlobalFunction2() {  
   CMyClass c = {2.0};  
   throw c;  
}  
  
int main() {  
   for ( int i = 1; i >= 0; --i ) {  
      try {  
         if ( i == 1 )  
            GlobalFunction2();  
         if ( i == 0 )  
            GlobalFunction();  
      }  
      catch ( CMyClass& catchC ) {  
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );  
         Console::WriteLine( catchC.d );  
      }  
      catch ( MyStruct^ catchException ) {  
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );  
         Console::WriteLine( catchException->i );  
      }  
   }  
}  
```  
  
### Resultados  
  
```  
In 'catch(CMyClass& catchC)'  
2  
In 'catch(MyStruct^ catchException)'  
11  
```  
  
### Orden de Unwinding para objetos de C\+\+  
 El desenredo aparece para cualquier objeto de C\+\+ con destructores que pueden estar en la pila de tiempo de ejecución entre la función que produce y la función que administra.  Dado que asignan los tipos de CLR en la pila, desenredando no se aplica a ellos.  
  
 El orden de los eventos para una excepción es el siguiente:  
  
1.  El tiempo de ejecución recorre la pila que busca la cláusula adecuada catch, o en el caso de SEH, excepto el filtro para SEH, para detectar la excepción.  Las cláusulas catch se buscan primero en orden léxico, y a continuación dinámicamente inferior de la pila de llamadas.  
  
2.  Encuentran una vez el controlador correcto, la pila se desenreda hasta ese punto.  Para cada llamada de función en la pila, sus objetos locales destruyan y \_\_finally bloques se ejecutan, externa más anidado.  
  
3.  Una vez que se desenreda la pila, se ejecuta la cláusula catch.  
  
### Tipos no administrados de detección  
 Cuando producen un tipo de objeto no administrado, se ajusta con una excepción de [System::Runtime.InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx)escrito.  Al buscar la cláusula adecuada de **catch** , hay dos posibilidades.  
  
-   Si se encuentra un tipo de C\+\+ nativo, la excepción se desempaqueta y se compara con el tipo encontrado.  Esta comparación permite que detectan a un tipo nativo de C\+\+ de la manera normal.  
  
-   Sin embargo, si una cláusula de **catch** de **SEHException** cualquiera de cualquiera de sus clases base se examina primero, la cláusula interceptará la excepción.  Por consiguiente, debe colocar todas las cláusulas catch que detectan los tipos de C\+\+ nativo antes de cualquier cláusula catch de tipos CLR.  
  
 Tenga en cuenta lo siguiente:  
  
```  
catch(Object^)  
```  
  
 y  
  
```  
catch(...)  
```  
  
 ambos detectan el tipo se produce incluidas excepciones de SEH.  
  
 Si la captura \(Object^\) detecta un tipo no administrado, no destruirá el objeto iniciado.  
  
 Cuando las excepciones no administradas que producen o detecten, se recomienda usa la opción del compilador [\/EHsc](../build/reference/eh-exception-handling-model.md) en lugar de **\/EHs** o de **\/EHa**.  
  
## Vea también  
 [Control de excepciones](../windows/exception-handling-cpp-component-extensions.md)   
 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)