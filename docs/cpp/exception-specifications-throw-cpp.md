---
title: Especificaciones de excepciones (throw) (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions, exception specifications
- throwing exceptions, throw keyword
- C++ exception handling, throwing exceptions
- throw keyword [C++], throw() vs. throw(...)
- throw keyword [C++], exception specifications
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 6577cf489ee1c9d64689938bb8a12660cec96893
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="exception-specifications-throw-noexcept-c"></a>Especificaciones de excepciones (throw, noexcept) (C++)
Las especificaciones de excepción son una característica del lenguaje C++ que indican la intención del programador acerca de los tipos de excepción que se puede propagar una función. Puede especificar que una función puede o no puede cerrarse debido a una excepción utilizando una *una especificación de excepción*. El compilador puede utilizar esta información para optimizar las llamadas a la función y la función de secuencias de escape de que finalice el programa si una excepción inesperada. Hay dos tipos de especificación de excepción. El *noexcept especificación* es nueva en C ++ 11. Especifica si el conjunto de posibles excepciones que puedan salir de la función está vacío. El *una especificación de excepción dinámica*, o `throw(optional_type_list)` specification, está en desuso en C ++ 11 y Visual Studio admite solo parcialmente. Esta especificación de excepción se diseñó para proporcionar información de resumen sobre qué excepciones se pueden iniciar desde una función, pero en la práctica resultaron para ser problemáticas. Una especificación de excepción dinámica que resultó útil de alguna manera fue el incondicional `throw()` especificación. Por ejemplo, la declaración de función:  
  
```cpp  
void MyFunction(int i) throw();  
```  
  
 indica al compilador que la función no produce ninguna excepción. Es el equivalente a usar [__declspec (nothrow)](../cpp/nothrow-cpp.md). Su uso se considera opcional.  
  
En el ISO C ++ 11 estándar, el [noexcept](../cpp/noexcept-cpp.md) operador se introdujo como un reemplazo. Se admite en Visual Studio 2015 y versiones posteriores. Siempre que sea posible, utilice un `noexcept` expresión para especificar si una función puede producir excepciones. Por ejemplo, use esta declaración de función en lugar de la anterior:  
  
```cpp  
void MyFunction(int i) noexcept;  
```  
  
Aunque Visual C++ es totalmente compatible con la `noexcept` expresión, se sale de la norma ISO de C++ en su implementación de las especificaciones de excepción dinámica.  La tabla siguiente resume la implementación de Visual C++ de las especificaciones de excepciones:  
  
|Especificación de la excepción|Significado|  
|-----------------------------|-------------|  
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|La función no produce ninguna excepción. Sin embargo, si se produce una excepción fuera de una función marcada `throw()`, el compilador de Visual C++ llama `std::terminate`, no `std::unexpected`. Vea [std::unexpected](../c-runtime-library/reference/unexpected-crt.md) para obtener más información. Si una función está marcada como `noexcept`, `noexcept(true)`, o `throw()`, el compilador de Visual C++ supone que la función no produce excepciones de C++ y genera el código en consecuencia. Dado que pueden realizar optimizaciones de código que el compilador de C++ basado en la suposición de que la función no produce ninguna excepción de C++, si una función produce una excepción, el programa puede no ejecutarse correctamente.|  
|`noexcept(false)`<br/>`throw(...)`<br/>Ninguna especificación|La función puede producir una excepción de cualquier tipo.|  
|`throw(type)`|La función puede producir una excepción del tipo `type`. En Visual C++, se acepta esta sintaxis, pero se interpreta como `noexcept(false)`.|  
  
 Si se usa el control de excepciones en una aplicación, debe haber una función en la pila de llamadas que controla las excepciones se produce antes de salir del ámbito de una función externo marcado `noexcept`, `noexcept(true)`, o `throw()`. Si llama a las funciones entre la que se produce una excepción y que controla la excepción se especifican como `noexcept`, `noexcept(true)`, o `throw()`, el programa finaliza cuando la función noexcept propaga la excepción.  
  
 El comportamiento de excepción de una función depende de los siguientes factores:  
  
-   Si está compilando la función con C o C++.  
  
-   Que [/EH](../build/reference/eh-exception-handling-model.md) opción de compilador que se utiliza.  
  
-   Si ha especificado explícitamente la especificación de la excepción.  
  
 Las especificaciones de excepciones explícitas no se permiten en las funciones de C. Una función de C se supone que no producen excepciones en **/EHsc**y pueden producir las excepciones estructuradas en **/EHs**, **/EHa**, o **/EHac**.  
  
 En la tabla siguiente resume si una función de C++ puede producir potencialmente en diversas opciones de control de excepciones de compilador:  
  
|Función|/EHsc|/EHs|/EHa|/EHac|  
|--------------|------------|-----------|-----------|------------|  
|Función de C++ sin especificación de excepciones|Sí|Sí|Sí|Sí|  
|Función de C++ con `noexcept`, `noexcept(true)`, o `throw()` una especificación de excepción|No|No|Sí|Sí|  
|Función de C++ con `noexcept(false)`, `throw(...)`, o `throw(type)` una especificación de excepción|Sí|Sí|Sí|Sí|  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// exception_specification.cpp  
// compile with: /EHs  
#include <stdio.h>  
  
void handler() {  
   printf_s("in handler\n");  
}  
  
void f1(void) throw(int) {  
   printf_s("About to throw 1\n");  
   if (1)  
      throw 1;  
}  
  
void f5(void) throw() {  
   try {  
      f1();  
   }  
   catch(...) {  
      handler();  
    }  
}  
  
// invalid, doesn't handle the int exception thrown from f1()  
// void f3(void) throw() {  
//   f1();  
// }  
  
void __declspec(nothrow) f2(void) {  
   try {  
      f1();  
   }  
   catch(int) {  
      handler();  
    }  
}  
  
// only valid if compiled without /EHc   
// /EHc means assume extern "C" functions don't throw exceptions  
extern "C" void f4(void);  
void f4(void) {  
   f1();  
}  
  
int main() {  
   f2();  
  
   try {  
      f4();  
   }  
   catch(...) {  
      printf_s("Caught exception from f4\n");  
   }  
   f5();  
}  
```  
  
```Output  
About to throw 1  
in handler  
About to throw 1  
Caught exception from f4  
About to throw 1  
in handler  
```  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones try, throw y catch (C++)](../cpp/try-throw-and-catch-statements-cpp.md)   
 [Control de excepciones de C++](../cpp/cpp-exception-handling.md)
