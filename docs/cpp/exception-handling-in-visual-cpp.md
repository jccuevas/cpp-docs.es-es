---
title: Exception handling in MSVC
ms.date: 11/19/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 6cf71d6e6d0519951a084ebead65003bd363395f
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246586"
---
# <a name="exception-handling-in-msvc"></a>Exception handling in MSVC

Una excepción es una condición de error, posiblemente fuera del control del programa, que evita que el programa continúe a lo largo de su ruta normal de ejecución. Determinadas operaciones, incluidas la creación de objetos, la entrada/salida de archivo y las llamadas de función realizadas desde otros módulos, son posibles orígenes de excepciones aunque el programa se ejecute correctamente. Un código robusto prevé y controla las excepciones. To detect logic errors, use assertions rather than exceptions (see [Using Assertions](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Kinds of exceptions

The Microsoft C++ compiler (MSVC) supports three kinds of exception handling:

- [C++ exception handling](errors-and-exception-handling-modern-cpp.md)

   Para la mayoría de los programas de C++, se debe utilizar el control de excepciones de C++, que tiene seguridad de tipos y garantiza que se llame a los destructores de objeto durante el desenredo de la pila.

- [Structured exception handling](structured-exception-handling-c-cpp.md)

   Windows suministra su propio mecanismo de excepción, denominado SEH. No se recomienda para la programación con C++ o con MFC. Use SEH only in non-MFC C programs.

- [MFC exceptions](../mfc/exception-handling-in-mfc.md)

Use the [/EH](../build/reference/eh-exception-handling-model.md) compiler option to specify the type of exception handling to use in a project; C++ exception handling is the default. No combine los mecanismos de control de errores; por ejemplo, no use las excepciones de C++ con control de excepciones estructurado. Si usa el control de excepciones de C++, el código será más portátil y podrá controlar todo tipo de excepciones. For more information about the drawbacks of structured exception handling, see [Structured Exception Handling](structured-exception-handling-c-cpp.md). For advice about mixing MFC macros and C++ exceptions, see [Exceptions: Using MFC Macros and C++ Exceptions](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>En esta sección

- [Modern C++ best practices for exceptions and error handling](errors-and-exception-handling-modern-cpp.md)

- [How to design for exception safety](how-to-design-for-exception-safety.md)

- [How to interface between exceptional and non-exceptional code](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [The try, catch, and throw Statements](try-throw-and-catch-statements-cpp.md)

- [Cómo se evalúan los bloques Catch](how-catch-blocks-are-evaluated-cpp.md)

- [Exceptions and Stack Unwinding](exceptions-and-stack-unwinding-in-cpp.md)

- [Exception Specifications](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Excepciones de C++ no controladas](unhandled-cpp-exceptions.md)

- [Mezclar excepciones de C (estructuradas) y de C++](mixing-c-structured-and-cpp-exceptions.md)

- [Structured Exception Handling (SEH) (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](cpp-language-reference.md)</br>
[Control de excepciones x64](../build/exception-handling-x64.md)</br>
[Exception Handling (C++/CLI and C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
