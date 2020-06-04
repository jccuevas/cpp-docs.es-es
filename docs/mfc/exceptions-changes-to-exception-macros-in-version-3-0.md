---
title: 'Excepciones: Cambios en las macros de excepción en la versión 3.0'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 82320b0c7ccd6766e016f0437633339f8f8f61d6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365493"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>Excepciones: Cambios en las macros de excepción en la versión 3.0

Este es un tema avanzado.

En MFC versión 3.0 y versiones posteriores, las macros de control de excepciones se han cambiado para usar excepciones De C++. En este artículo se explica cómo esos cambios pueden afectar al comportamiento del código existente que usa las macros.

En este artículo se tratan los temas siguientes:

- [Tipos de excepción y la macro CATCH](#_core_exception_types_and_the_catch_macro)

- [Volver a lanzar excepciones](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a>Tipos de excepción y la macro CATCH

En versiones anteriores de MFC, la macro **CATCH** usaba información de tipo en tiempo de ejecución MFC para determinar el tipo de una excepción; el tipo de la excepción se determina, en otras palabras, en el sitio de captura. Con las excepciones de C++, sin embargo, el tipo de la excepción siempre se determina en el sitio de inicio por el tipo del objeto de excepción que se produce. Esto provocará incompatibilidades en el caso poco frecuente donde el tipo del puntero al objeto lanzado difiere del tipo del objeto lanzado.

En el ejemplo siguiente se muestra la consecuencia de esta diferencia entre MFC versión 3.0 y versiones anteriores:

[!code-cpp[NVC_MFCExceptions#1](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

Este código se comporta de forma diferente en la versión 3.0 porque el control siempre pasa al primer bloque **catch** con una declaración de excepción coincidente. El resultado de la expresión throw

[!code-cpp[NVC_MFCExceptions#19](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

se lanza como `CException*`un , a pesar `CCustomException`de que se construye como un . La macro **CATCH** en las versiones `CObject::IsKindOf` 2.5 y anteriores de MFC se usa para probar el tipo en tiempo de ejecución. Porque la expresión

[!code-cpp[NVC_MFCExceptions#20](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

es cierto, el primer bloque catch detecta la excepción. En la versión 3.0, que utiliza excepciones C++ para implementar muchas de `CException`las macros de control de excepciones, el segundo bloque catch coincide con el producido.

Un código como este es poco común. Normalmente aparece cuando se pasa un objeto de `CException*`excepción a otra función que acepta un procesamiento genérico, realiza el procesamiento "pre-throw" y, finalmente, produce la excepción.

Para evitar este problema, mueva la expresión throw de la función al código de llamada y produzca una excepción del tipo real conocido por el compilador en el momento en que se genera la excepción.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a>Volver a lanzar excepciones

Un bloque catch no puede producir el mismo puntero de excepción que detectó.

Por ejemplo, este código era válido en versiones anteriores, pero tendrá resultados inesperados con la versión 3.0:

[!code-cpp[NVC_MFCExceptions#2](../mfc/codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

El uso de **THROW** en `e` el bloque catch hace que se elimine el puntero, de modo que el sitio de captura externo recibirá un puntero no válido. Utilice **THROW_LAST** para `e`volver a lanzar .

Para obtener más información, vea [Excepciones: captura y eliminación](../mfc/exceptions-catching-and-deleting-exceptions.md)de excepciones .

## <a name="see-also"></a>Consulte también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
