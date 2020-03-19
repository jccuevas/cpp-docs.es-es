---
title: Especificaciones de excepciones (Throw, noexception)C++()
ms.date: 01/18/2018
helpviewer_keywords:
- exceptions [C++], exception specifications
- throwing exceptions [C++], throw keyword
- C++ exception handling [C++], throwing exceptions
- throw keyword [C++]
- noexcept keyword [C++]
ms.assetid: 4d3276df-6f31-4c7f-8cab-b9d2d003a629
ms.openlocfilehash: 4c7cc6027a3af4c300b88389cb29e3ccf091514e
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509422"
---
# <a name="exception-specifications-throw-noexcept-c"></a>Especificaciones de excepciones (Throw, noexception)C++()

Las especificaciones de excepción C++ son una característica de lenguaje que indica la intención del programador sobre los tipos de excepción que se pueden propagar por una función. Puede especificar que una función pueda o no salir mediante una excepción mediante una *especificación de excepción*. El compilador puede utilizar esta información para optimizar las llamadas a la función y para finalizar el programa si una excepción inesperada escapa a la función.

Antes de C++ 17 había dos tipos de especificación de excepción. La *especificación noexception* era nueva en c++ 11. Especifica si el conjunto de excepciones potenciales que puede escapar la función está vacío. La *especificación de excepción dinámica*, o la especificación `throw(optional_type_list)`, quedó en desuso en c++ 11 y se quitó en c++ 17, salvo `throw()`, que es un alias para `noexcept(true)`. Esta especificación de excepción se diseñó para proporcionar información de resumen sobre qué excepciones se pueden iniciar desde una función, pero en la práctica se ha descubierto que es problemática. La especificación de la excepción dinámica que ha demostrado ser algo útil era la especificación de `throw()` incondicional. Por ejemplo, la declaración de función:

```cpp
void MyFunction(int i) throw();
```

indica al compilador que la función no produce ninguna excepción. Sin embargo, en el modo **/STD: c++ 14** esto podría provocar un comportamiento indefinido si la función produce una excepción. Por lo tanto, se recomienda usar el operador [noexception](../cpp/noexcept-cpp.md) en lugar de uno anterior:

```cpp
void MyFunction(int i) noexcept;
```

En la tabla siguiente se resume C++ la implementación de Microsoft de especificaciones de excepciones:

|Especificación de la excepción|Significado|
|-----------------------------|-------------|
|`noexcept`<br/>`noexcept(true)`<br/>`throw()`|La función no produce ninguna excepción. En [/STD: modo c++ 14](../build/reference/std-specify-language-standard-version.md) (que es el valor predeterminado), `noexcept` y `noexcept(true)` son equivalentes. Cuando se produce una excepción de una función que se declara `noexcept` o `noexcept(true)`, se invoca [STD:: Terminate](../standard-library/exception-functions.md#terminate) . Cuando se produce una excepción desde una función declarada como `throw()` en el modo **/STD: c++ 14** , el resultado es un comportamiento indefinido. No se invoca ninguna función específica. Se trata de una divergencia con respecto al estándar de C++ 14, que requiere que el compilador invoque [STD:: inesperado](../standard-library/exception-functions.md#unexpected).  <br/> **Visual Studio 2017 versión 15,5 y posteriores**: en **/STD: el modo c++ 17** , `noexcept`, `noexcept(true)`y `throw()` son equivalentes. En el modo **/STD: c++ 17** , `throw()` es un alias de `noexcept(true)`. En el modo **/STD: c++ 17** , cuando se produce una excepción desde una función declarada con cualquiera de estas especificaciones, se invoca [STD:: Terminate](../standard-library/exception-functions.md#terminate) como requiere el estándar c++ 17.|
|`noexcept(false)`<br/>`throw(...)`<br/>Sin especificación|La función puede producir una excepción de cualquier tipo.|
|`throw(type)`| (**C++ 14 y versiones anteriores**) La función puede producir una excepción de tipo `type`. El compilador acepta la sintaxis, pero lo interpreta como `noexcept(false)`. En el modo **/STD: c++ 17** , el compilador emite la advertencia C5040.|

Si se usa el control de excepciones en una aplicación, debe haber una función en la pila de llamadas que controle las excepciones iniciadas antes de salir del ámbito externo de una función marcada como `noexcept`, `noexcept(true)`o `throw()`. Si alguna función llamada entre la que produce una excepción y la que controla la excepción se especifican como `noexcept`, `noexcept(true)` (o `throw()` en el modo **/STD: c++ 17** ), el programa se termina cuando la función noexception propaga la excepción.

El comportamiento de excepción de una función depende de los siguientes factores:

- El [modo de compilación estándar de lenguaje](../build/reference/std-specify-language-standard-version.md) que se establece.
- Si está compilando la función con C o C++.

- Qué opción del compilador [/EH](../build/reference/eh-exception-handling-model.md) se usa.

- Si ha especificado explícitamente la especificación de la excepción.

Las especificaciones de excepciones explícitas no se permiten en las funciones de C. Se supone que una función de C produce excepciones en **/EHsc**y puede producir excepciones estructuradas en **/EHS**, **/EHA**o **/EHac**.

En la tabla siguiente se resume C++ si una función puede producirse en diversas opciones de control de excepciones del compilador:

|Función|/EHsc|/EHs|/EHa|/EHac|
|--------------|------------|-----------|-----------|------------|
|Función de C++ sin especificación de excepciones|Sí|Sí|Sí|Sí|
|C++función con `noexcept`, `noexcept(true)`o `throw()` especificación de la excepción|No|No|Sí|Sí|
|C++función con `noexcept(false)`, `throw(...)`o `throw(type)` especificación de la excepción|Sí|Sí|Sí|Sí|

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

## <a name="see-also"></a>Consulte también

[Instrucciones try, throw y catch (C++)](../cpp/try-throw-and-catch-statements-cpp.md)<br/>
[Prácticas C++ recomendadas modernas para excepciones y control de errores](errors-and-exception-handling-modern-cpp.md)