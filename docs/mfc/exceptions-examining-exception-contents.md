---
title: 'Excepciones: Examinar contenidos de excepciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 06d33c021d5bb7e802a9aba362fcd0152ff5eab0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="exceptions-examining-exception-contents"></a>Excepciones: Examinar contenidos de excepciones
Aunque un **catch** argumento del bloque puede ser de casi cualquier tipo de datos, las funciones MFC inician excepciones de tipos derivados de la clase `CException`. Para detectar una excepción producida por una función MFC, a continuación, se escribe un **catch** bloque cuyo argumento es un puntero a un `CException` objeto (o un objeto derivado de `CException`, como `CMemoryException`). Según el tipo exacto de la excepción, puede examinar los miembros de datos del objeto de excepción para recopilar información sobre la causa específica de la excepción.  
  
 Por ejemplo, el `CFileException` tipo tiene el `m_cause` miembro de datos, que contiene un tipo enumerado que especifica la causa de la excepción de archivo. Algunos ejemplos de los posibles valores devuelven son **CFileException** y **CFileException:: ReadOnly**.  
  
 En el ejemplo siguiente se muestra cómo examinar el contenido de un `CFileException`. Otros tipos de excepción pueden examinarse de forma similar.  
  
 [!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]  
  
 Para obtener más información, consulte [excepciones: liberar objetos en excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md) y [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

