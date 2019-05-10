---
title: Control de excepciones en MSVC
ms.date: 05/07/2019
helpviewer_keywords:
- try-catch keyword [C++], exception handling
ms.assetid: a6aa08de-669d-4ce8-9ec3-ec20d1354fcf
ms.openlocfilehash: 47443f1b7021aac7755d77f797a4f7b7410281f8
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222063"
---
# <a name="exception-handling-in-msvc"></a>Control de excepciones en MSVC

Una excepción es una condición de error, posiblemente fuera del control del programa, que evita que el programa continúe a lo largo de su ruta normal de ejecución. Determinadas operaciones, incluidas la creación de objetos, la entrada/salida de archivo y las llamadas de función realizadas desde otros módulos, son posibles orígenes de excepciones aunque el programa se ejecute correctamente. Un código robusto prevé y controla las excepciones.

Para detectar errores lógicos dentro de un programa o un módulo, utilice aserciones en lugar de excepciones (vea [utilizar aserciones](/visualstudio/debugger/c-cpp-assertions)).

Microsoft C++ compilador (MSVC) admite tres tipos de control de excepciones:

- [Control de excepciones de C++](../cpp/cpp-exception-handling.md)

   Para la mayoría de los programas de C++, se debe utilizar el control de excepciones de C++, que tiene seguridad de tipos y garantiza que se llame a los destructores de objeto durante el desenredo de la pila.

- [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)

   Windows suministra su propio mecanismo de excepción, denominado SEH. No se recomienda para la programación con C++ o con MFC. Utilice SEH sólo en programas de C que no son de MFC.

- [Excepciones de MFC](../mfc/exception-handling-in-mfc.md)

   Desde la versión 3.0, MFC ha utilizado las excepciones de C++ pero sigue admitiendo sus anteriores macros de control de excepciones, que son similares a las excepciones de C++ en su forma. Aunque estas macros no son recomendables para nueva programación, todavía se siguen admitiendo por razones de compatibilidad con versiones anteriores. En los programas que ya utilizan las macros, también puede utilizar libremente las excepciones de C++. Durante el preprocesamiento, las macros evalúan las palabras clave definidas en la implementación de MSVC de control de excepciones del C++ lenguaje a partir de Visual C++ versión 2.0. Puede dejar las macros de excepciones existentes en su sitio mientras empieza a utilizar las excepciones de C++.

Utilice la [/EH](../build/reference/eh-exception-handling-model.md) opción del compilador para especificar el tipo de control de excepciones para usar en un proyecto; Control de excepciones de C++ es el valor predeterminado. No combine los mecanismos de control de errores; por ejemplo, no use las excepciones de C++ con control de excepciones estructurado. Si usa el control de excepciones de C++, el código será más portátil y podrá controlar todo tipo de excepciones. Para obtener más información sobre los inconvenientes de control de excepciones estructurado, consulte [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). Para obtener más información sobre la combinación de macros de MFC y excepciones de C++, consulte [Excepciones: Uso de macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

Para obtener información sobre cómo controlar las excepciones en aplicaciones de CLR, vea [control de excepciones (C++ / c++ / CLI y c++ / CX)](../extensions/exception-handling-cpp-component-extensions.md).

Para obtener información sobre el control de excepciones en x64 procesadores, consulte [x64 control de excepciones](../build/exception-handling-x64.md).

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)