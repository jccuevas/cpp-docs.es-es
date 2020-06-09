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
ms.openlocfilehash: d669c58da04a1cd0ead424d93f6fad6adcd4c56c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622734"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Excepciones: Usar macros de MFC y excepciones de C++

En este artículo se tratan las consideraciones para escribir código que usa las macros de control de excepciones de MFC y las palabras clave de control de excepciones de C++.

En este artículo se tratan los temas siguientes:

- [Mezclar palabras clave y macros de excepción](#_core_mixing_exception_keywords_and_macros)

- [Bloques try dentro de bloques Catch](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a>Mezclar palabras clave y macros de excepción

Puede mezclar macros de excepción de MFC y palabras clave de excepciones de C++ en el mismo programa. Pero no se pueden mezclar macros de MFC con palabras clave de excepciones de C++ en el mismo bloque porque las macros eliminan automáticamente los objetos de excepción cuando salen del ámbito, mientras que el código que usa las palabras clave de control de excepciones no. Para obtener más información, vea el artículo [excepciones: detectar y eliminar excepciones](exceptions-catching-and-deleting-exceptions.md).

La diferencia principal entre las macros y las palabras clave es que las macros "automáticamente" eliminan una excepción detectada cuando la excepción sale del ámbito. El código que usa las palabras clave no lo hace; las excepciones detectadas en un bloque catch deben eliminarse explícitamente. La combinación de macros y palabras clave de excepciones de C++ puede producir pérdidas de memoria cuando no se elimina un objeto de excepción o daños en el montón cuando se elimina dos veces una excepción.

Por ejemplo, el código siguiente invalida el puntero de excepción:

[!code-cpp[NVC_MFCExceptions#10](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

El problema se produce porque `e` se elimina cuando la ejecución sale del bloque **catch** "interno". El uso de la macro **THROW_LAST** en lugar de la instrucción **Throw** hará que el bloque **catch** "externo" reciba un puntero válido:

[!code-cpp[NVC_MFCExceptions#11](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a>Bloques try dentro de bloques Catch

No se puede volver a producir la excepción actual desde dentro de un bloque **try** que está dentro de un bloque **catch** . El siguiente ejemplo no es válido:

[!code-cpp[NVC_MFCExceptions#12](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Para obtener más información, vea [excepciones: examinar el contenido](exceptions-examining-exception-contents.md)de las excepciones.

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
