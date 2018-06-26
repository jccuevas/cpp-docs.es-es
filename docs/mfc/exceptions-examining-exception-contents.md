---
title: 'Excepciones: Examinar contenidos de excepciones | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82c7453b92ce14fbbcd20ea0f9a8bd8a7a2b5b6d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932239"
---
# <a name="exceptions-examining-exception-contents"></a>Excepciones: Examinar contenidos de excepciones
Aunque un **catch** argumento del bloque puede ser de casi cualquier tipo de datos, las funciones MFC inician excepciones de tipos derivados de la clase `CException`. Para detectar una excepción producida por una función MFC, a continuación, se escribe un **catch** bloque cuyo argumento es un puntero a un `CException` objeto (o un objeto derivado de `CException`, como `CMemoryException`). Según el tipo exacto de la excepción, puede examinar los miembros de datos del objeto de excepción para recopilar información sobre la causa específica de la excepción.  
  
 Por ejemplo, el `CFileException` tipo tiene el `m_cause` miembro de datos, que contiene un tipo enumerado que especifica la causa de la excepción de archivo. Algunos ejemplos de los posibles valores devuelven son `CFileException::fileNotFound` y `CFileException::readOnly`.  
  
 En el ejemplo siguiente se muestra cómo examinar el contenido de un `CFileException`. Otros tipos de excepción pueden examinarse de forma similar.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 Para obtener más información, consulte [excepciones: liberar objetos en excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md) y [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

