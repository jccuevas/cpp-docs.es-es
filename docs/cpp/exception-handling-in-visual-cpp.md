---
title: Manejo de excepciones en MSVC
description: Descripción general del control de excepciones de referencia de idioma C++.
ms.date: 04/15/2020
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 0d60f49c6f1412925c19aaf497352940411b5d92
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396282"
---
# <a name="exception-handling-in-msvc"></a>Manejo de excepciones en MSVC

Una excepción es una condición de error, posiblemente fuera del control del programa, que evita que el programa continúe a lo largo de su ruta normal de ejecución. Ciertas operaciones, incluidas la creación de objetos, la entrada/salida de archivos y las llamadas a funciones realizadas desde otros módulos, son todas las posibles fuentes de excepciones, incluso cuando el programa se está ejecutando correctamente. Un código robusto prevé y controla las excepciones. Para detectar errores lógicos, utilice aserciones en lugar de excepciones (consulte Uso de [aserciones](/visualstudio/debugger/c-cpp-assertions)).

## <a name="kinds-of-exceptions"></a>Tipos de excepciones

El compilador de Microsoft C++ (MSVC) admite tres tipos de control de excepciones:

- [Control de excepciones C++](errors-and-exception-handling-modern-cpp.md)

   Para la mayoría de los programas C++, debe usar el control de excepciones C++. Es seguro para tipos y garantiza que los destructores de objetos se invocan durante el desenredado de la pila.

- [Control de excepciones estructurado](structured-exception-handling-c-cpp.md)

   Windows proporciona su propio mecanismo de excepción, denominado control de excepciones estructurado (SEH). No se recomienda para la programación C++ o MFC. SEH solo debe utilizarse en programas que no son de MFC C.

- [Excepciones de MFC](../mfc/exception-handling-in-mfc.md)

   Desde la versión 3.0, MFC ha utilizado excepciones C++. Todavía admite sus macros de control de excepciones más antiguas, que son similares a las excepciones C+ + en forma. Para obtener información sobre cómo mezclar macros MFC y excepciones C++, vea [Excepciones: uso de macros MFC y excepciones C++.](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

Utilice una opción del compilador [/EH](../build/reference/eh-exception-handling-model.md) para especificar el modelo de control de excepciones que se usará en un proyecto de C++. El control de excepciones estándar de C++ (**/EHsc**) es el valor predeterminado en los nuevos proyectos de C++ en Visual Studio.

No se recomienda mezclar los mecanismos de control de excepciones. Por ejemplo, no use excepciones C++ con control de excepciones estructurado. El uso exclusivo del control de excepciones de C++ hace que el código sea más portátil y le permite controlar excepciones de cualquier tipo. Para obtener más información acerca de los inconvenientes del control de excepciones estructurado, vea Control de [excepciones estructurado](structured-exception-handling-c-cpp.md).

## <a name="in-this-section"></a>En esta sección

- [Prácticas recomendadas modernas de C++ para excepciones y control de errores](errors-and-exception-handling-modern-cpp.md)

- [Cómo diseñar para la seguridad de excepciones](how-to-design-for-exception-safety.md)

- [Cómo: Interfaz entre código excepcional y no excepcional](how-to-interface-between-exceptional-and-non-exceptional-code.md)

- [Las instrucciones try, catch y throw](try-throw-and-catch-statements-cpp.md)

- [Cómo se evalúan los bloques catch](how-catch-blocks-are-evaluated-cpp.md)

- [Excepciones y desenredado de pilas](exceptions-and-stack-unwinding-in-cpp.md)

- [Especificaciones de excepción](exception-specifications-throw-cpp.md)

- [noexcept](noexcept-cpp.md)

- [Excepciones de C++ no controladas](unhandled-cpp-exceptions.md)

- [Mezclar excepciones de C (estructuradas) y de C++](mixing-c-structured-and-cpp-exceptions.md)

- [Control de excepciones estructurado (C/C++)](structured-exception-handling-c-cpp.md)

## <a name="see-also"></a>Consulte también

[Referencia del idioma C++](cpp-language-reference.md)</br>
[Control de excepciones x64](../build/exception-handling-x64.md)</br>
[Manejo de excepciones (C++/CLI y C++/CX)](../extensions/exception-handling-cpp-component-extensions.md)
