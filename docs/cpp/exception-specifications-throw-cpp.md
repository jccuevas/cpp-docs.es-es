---
title: Especificaciones de excepciones (throw, noexcept) (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bd96f666c4733f1c9b1aff65705840a46729194c
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="exception-specifications-throw-noexcept-c"></a>Especificaciones de excepciones (throw, noexcept) (C++)

Las especificaciones de excepción son una característica del lenguaje C++ que indican la intención del programador acerca de los tipos de excepción que se puede propagar una función. Puede especificar que una función puede o no puede cerrarse debido a una excepción utilizando una *una especificación de excepción*. El compilador puede utilizar esta información para optimizar las llamadas a la función y la función de secuencias de escape de que finalice el programa si una excepción inesperada. 

Antes de C ++ 17, hay dos tipos de especificación de excepción. El *noexcept especificación* era nuevo en C ++ 11. Especifica si el conjunto de posibles excepciones que puedan salir de la función está vacío. El *una especificación de excepción dinámica*, o `throw(optional_type_list)` se en desuso en C ++ 11 y se eliminó en C ++ 17, excepto para la especificación, `throw()`, que es un alias para `noexcept(true)`. Esta especificación de excepción se diseñó para proporcionar información de resumen sobre qué excepciones se pueden iniciar desde una función, pero en la práctica resultaron para ser problemáticas. Una especificación de excepción dinámica que resultó útil de alguna manera fue el incondicional `throw()` especificación. Por ejemplo, la declaración de función:

```cpp
void MyFunction(int i) throw();
```

 indica al compilador que la función no produce ninguna excepción. Sin embargo, en **/std:c ++ 14** modo podría producir un comportamiento no definido si la función produce una excepción. Por lo tanto, se recomienda utilizar la [noexcept](../cpp/noexcept-cpp.md) operador en lugar del anterior:

```cpp
void MyFunction(int i) noexcept;
```

La tabla siguiente resume la implementación de Visual C++ de las especificaciones de excepciones:

|Especificación de la excepción|Significado|
|-----------------------------|-------------|
|`noexcept`<br>`noexcept(true)`<br>`throw()`|La función no produce ninguna excepción. En [/std:c ++ 14](../build/reference/std-specify-language-standard-version.md) modo (que es el valor predeterminado), `noexcept` y `noexcept(true)` son equivalentes. Cuando se produce una excepción desde una función que se declara `noexcept` o `noexcept(true)`, [std:: Terminate](../standard-library/exception-functions.md#terminate) se invoca. Cuando se produce una excepción desde una función declarada como `throw()` en **/std:c ++ 14** modo, el resultado es un comportamiento indefinido. No se invoca ninguna función específica. Se trata de una divergencia de 14 de C++ estándar, que requiere el compilador invoque [std::unexpected](../standard-library/exception-functions.md#unexpected).  <br> **Visual Studio 2017 15.5 y versiones posteriores**: en **/std:c ++ 17** modo, `noexcept`, `noexcept(true)`, y `throw()` son equivalentes. En **/std:c ++ 17** modo, `throw()` es un alias para `noexcept(true)`. En **/std:c ++ 17** modo, cuando se produce una excepción desde una función declarada con cualquiera de estas especificaciones, [std:: Terminate](../standard-library/exception-functions.md#terminate) se invoca según lo solicitado por el estándar C ++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Ninguna especificación|La función puede producir una excepción de cualquier tipo.|
|`throw(type)`| (**C ++ 14 y versiones anteriores**) la función puede producir una excepción de tipo `type`. El compilador de Microsoft C++ acepta la sintaxis, pero lo interpreta como `noexcept(false)`. En **/std:c ++ 17** modo el compilador emite la advertencia C5040.|

 Si se usa el control de excepciones en una aplicación, debe haber una función en la pila de llamadas que controla las excepciones se produce antes de salir del ámbito de una función externo marcado `noexcept`, `noexcept(true)`, o `throw()`. Si llama a las funciones entre la que se produce una excepción y que controla la excepción se especifican como `noexcept`, `noexcept(true)` (o `throw()` en **/std:c ++ 17** modo), el programa finaliza cuando el función noexcept propaga la excepción.

 El comportamiento de excepción de una función depende de los siguientes factores:

- Que [modo de compilación estándar de lenguaje](../build/reference/std-specify-language-standard-version.md) se establece.
- Si está compilando la función con C o C++.

- Que [/EH](../build/reference/eh-exception-handling-model.md) opción de compilador que se utiliza.

- Si ha especificado explícitamente la especificación de la excepción.

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

 [try, throw y catch instrucciones (C++)](../cpp/try-throw-and-catch-statements-cpp.md) [control de excepciones de C++](../cpp/cpp-exception-handling.md)