---
title: 'Excepciones: Usar macros de MFC y excepciones de C++'
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: afad5335bedf001329ecb401a8a16c663afb5571
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371587"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Excepciones: Usar macros de MFC y excepciones de C++

En este artículo se describen las consideraciones para escribir código que usa las macros de control de excepciones MFC y las palabras clave de control de excepciones de C++.

En este artículo se tratan los temas siguientes:

- [Mezcla de palabras clave y macros de excepción](#_core_mixing_exception_keywords_and_macros)

- [Pruebe bloques dentro de bloques de captura](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Mezcla de palabras clave de excepción y macros

Puede mezclar macros de excepción MFC y palabras clave de excepción C++ en el mismo programa. Pero no se pueden mezclar macros MFC con palabras clave de excepción C++ en el mismo bloque porque las macros eliminan objetos de excepción automáticamente cuando salen del ámbito, mientras que el código que usa las palabras clave de control de excepciones no lo hace. Para obtener más información, consulte el artículo [Excepciones: captura y eliminación](../mfc/exceptions-catching-and-deleting-exceptions.md)de excepciones .

La principal diferencia entre las macros y las palabras clave es que las macros eliminan "automáticamente" una excepción detectada cuando la excepción sale del ámbito. El código que usa las palabras clave no; las excepciones detectadas en un bloque catch deben eliminarse explícitamente. La mezcla de macros y palabras clave de excepción de C++ puede provocar pérdidas de memoria cuando no se elimina un objeto de excepción o daños en el montón cuando se elimina una excepción dos veces.

El código siguiente, por ejemplo, invalida el puntero de excepción:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

El problema `e` se produce porque se elimina cuando la ejecución sale del bloque **CATCH** "interno". El uso de la macro **THROW_LAST** en lugar de la instrucción **THROW** hará que el bloque **CATCH** "externo" reciba un puntero válido:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Prueba bloques dentro de los bloques catch

No se puede volver a iniciar la excepción actual desde dentro de un bloque **try** que está dentro de un bloque **CATCH.** El ejemplo siguiente no es válido:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Para obtener más información, vea [Excepciones: examen del contenido](../mfc/exceptions-examining-exception-contents.md)de excepciones .

## <a name="see-also"></a>Consulte también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
