---
title: 'Excepciones: Uso de Macros de MFC y excepciones de C++'
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
ms.openlocfilehash: 00e88ddabf3a8e8b591bebae7ebc8ced0e1dc637
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297715"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Excepciones: Uso de Macros de MFC y excepciones de C++

En este artículo se describe consideraciones para escribir código que utiliza las macros de control de excepciones de MFC y las palabras clave de control de excepciones de C++.

En este artículo se tratan los siguientes temas:

- [Mezclar macros y palabras clave de excepción](#_core_mixing_exception_keywords_and_macros)

- [Bloques try dentro de bloques catch](#_core_try_blocks_inside_catch_blocks)

##  <a name="_core_mixing_exception_keywords_and_macros"></a> Mezclar Macros y palabras clave de excepción

Puede mezclar macros de excepción de MFC y palabras clave de excepciones de C++ en el mismo programa. Pero no se pueden mezclar macros de MFC con palabras clave de excepciones de C++ en el mismo bloque porque las macros de eliminan objetos de excepción automáticamente cuando salen del ámbito, mientras que el código mediante las palabras clave de control de excepciones no lo hace. Para obtener más información, vea el artículo [excepciones: Detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).

La principal diferencia entre las macros y las palabras clave es que las macros eliminan "automáticamente" una excepción detectada cuando ésta sale del ámbito. Código mediante las palabras clave no lo hace; se deben eliminar explícitamente las excepciones detectadas en un bloque catch. Mezclar macros y palabras clave de excepciones de C++ puede causar pérdidas de memoria cuando no se elimina un objeto de excepción o daños en el montón cuando se elimina una excepción de dos veces.

El código siguiente, por ejemplo, invalida el puntero de la excepción:

[!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

El problema se produce porque `e` se elimina cuando la ejecución se transfiere "interno" **CATCH** bloque. Mediante el **THROW_LAST** macro en lugar de la **THROW** hará que la instrucción del "externa" **CATCH** bloque para recibir un puntero válido:

[!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

##  <a name="_core_try_blocks_inside_catch_blocks"></a> Pruebe los bloques dentro de bloques Catch

No puede volver a producir la excepción actual desde dentro un **intente** bloque que está dentro de un **CATCH** bloque. El ejemplo siguiente no es válido:

[!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

Para obtener más información, consulte [excepciones: Examinar contenidos de excepciones](../mfc/exceptions-examining-exception-contents.md).

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
