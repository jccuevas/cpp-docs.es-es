---
title: Control de excepciones en MSVC
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
# <a name="exception-handling-in-msvc"></a>Control de excepciones en MSVC

Una excepción es una condición de error, posiblemente fuera del control del programa, que evita que el programa continúe a lo largo de su ruta normal de ejecución. Determinadas operaciones, incluidas la creación de objetos, la entrada/salida de archivo y las llamadas de función realizadas desde otros módulos, son posibles orígenes de excepciones aunque el programa se ejecute correctamente. Un código robusto prevé y controla las excepciones. Para detectar errores lógicos, utilice aserciones en lugar de excepciones (vea [usar aserciones](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Tipos de excepciones

El compilador de Microsoft C++ (MSVC) admite tres tipos de control de excepciones:

- [C++control de excepciones](errors-and-exception-handling-modern-cpp.md)

   Para la mayoría de los programas de C++, se debe utilizar el control de excepciones de C++, que tiene seguridad de tipos y garantiza que se llame a los destructores de objeto durante el desenredo de la pila.

- [Control estructurado de excepciones](structured-exception-handling-c-cpp.md)

   Windows suministra su propio mecanismo de excepción, denominado SEH. No se recomienda para la programación con C++ o con MFC. Use SEH solo en programas que no son de MFC.

- [Excepciones de MFC](../mfc/exception-handling-in-mfc.md)

Use la opción del compilador [/EH](../build/reference/eh-exception-handling-model.md) para especificar el tipo de control de excepciones que se va a usar en un proyecto; C++ el control de excepciones es el valor predeterminado. No combine los mecanismos de control de errores; por ejemplo, no use las excepciones de C++ con control de excepciones estructurado. Si usa el control de excepciones de C++, el código será más portátil y podrá controlar todo tipo de excepciones. Para obtener más información sobre las desventajas del control de excepciones estructurado, vea [control de excepciones estructurado](structured-exception-handling-c-cpp.md). Para obtener consejos sobre cómo mezclar macros C++ y excepciones de MFC, vea [excepciones: usar macros y excepciones de C++ MFC](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="in-this-section"></a>En esta sección

- [Prácticas C++ recomendadas modernas para excepciones y control de errores](errors-and-exception-handling-modern-cpp.md)

- [Cómo diseñar para la seguridad de excepciones](how-to-design-for-exception-safety.md)

- [Cómo interactuar entre código excepcional y no excepcional](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Las instrucciones try, Catch y Throw](try-throw-and-catch-statements-cpp.md)

- [Cómo se evalúan los bloques Catch](how-catch-blocks-are-evaluated-cpp.md)

- [Excepciones y desenredo de la pila](exceptions-and-stack-unwinding-in-cpp.md)

- [Especificaciones de excepciones](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Excepciones de C++ no controladas](unhandled-cpp-exceptions.md)

- [Mezclar excepciones de C (estructuradas) y de C++](mixing-c-structured-and-cpp-exceptions.md)

- [Control de excepciones estructurado (SEH) (CC++/)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](cpp-language-reference.md)</br>
[Control de excepciones x64](../build/exception-handling-x64.md)</br>
[Control de excepcionesC++(/CLI C++y/CX)](../extensions/exception-handling-cpp-component-extensions.md)
