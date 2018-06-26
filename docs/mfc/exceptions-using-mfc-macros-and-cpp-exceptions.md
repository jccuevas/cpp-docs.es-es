---
title: 'Excepciones: Usar Macros MFC y las excepciones de C++ | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 698d8a754716f6876f9a72a0d5043807a32d2089
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932213"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>Excepciones: Usar macros de MFC y excepciones de C++
En este artículo se describe consideraciones para escribir código que utiliza las macros de control de excepciones de MFC y las palabras clave de control de excepciones de C++.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Cómo mezclar macros y palabras clave de excepción](#_core_mixing_exception_keywords_and_macros)  
  
-   [Bloques try dentro de bloques catch](#_core_try_blocks_inside_catch_blocks)  
  
##  <a name="_core_mixing_exception_keywords_and_macros"></a> Cómo mezclar Macros y palabras clave de excepción  
 Puede mezclar macros de excepción de MFC y palabras clave de excepciones de C++ en el mismo programa. Pero no se pueden mezclar macros de MFC con palabras clave de excepciones de C++ en el mismo bloque porque las macros eliminan objetos de excepción automáticamente cuando salen del ámbito, mientras que las palabras clave de control de excepciones de código no lo hace. Para obtener más información, vea el artículo [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 La diferencia principal entre las macros y las palabras clave es que las macros eliminan "automáticamente" una excepción detectada cuando ésta sale del ámbito. Código que utiliza las palabras clave no lo hace; las excepciones detectadas en un bloque catch se deben eliminar explícitamente. Cómo mezclar macros y palabras clave de excepción de C++ puede provocar pérdidas de memoria cuando no se elimina un objeto de excepción o daños en un montón cuando una excepción se elimina dos veces.  
  
 El código siguiente, por ejemplo, invalida el puntero de excepción:  
  
 [!code-cpp[NVC_MFCExceptions#10](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]  
  
 El problema se produce porque `e` se elimina cuando la ejecución se transfiere el "interno" **CATCH** bloque. Mediante el **THROW_LAST** macro en lugar de la **THROW** hará que la instrucción el "externo" **CATCH** bloque para recibir un puntero válido:  
  
 [!code-cpp[NVC_MFCExceptions#11](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]  
  
##  <a name="_core_try_blocks_inside_catch_blocks"></a> Intente bloques dentro de los bloques Catch  
 No puede volver a producir la excepción actual desde una **intente** bloque que está dentro de un **CATCH** bloque. En el ejemplo siguiente no es válido:  
  
 [!code-cpp[NVC_MFCExceptions#12](../mfc/codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]  
  
 Para obtener más información, consulte [excepciones: Examinar contenidos de excepciones](../mfc/exceptions-examining-exception-contents.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

