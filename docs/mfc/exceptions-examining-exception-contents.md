---
title: 'Excepciones: Examinar contenidos de excepciones'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: 8554dda2f465aa058cea3d257c22ec38bc6e2c18
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625903"
---
# <a name="exceptions-examining-exception-contents"></a>Excepciones: Examinar contenidos de excepciones

Aunque el argumento del bloque **catch** puede ser de casi cualquier tipo de datos, las funciones de MFC producen excepciones de tipos derivados de la clase `CException` . Para detectar una excepción producida por una función MFC, se escribe un bloque **catch** cuyo argumento es un puntero a un `CException` objeto (o un objeto derivado de, como `CException` `CMemoryException` ). Dependiendo del tipo exacto de la excepción, puede examinar los miembros de datos del objeto de excepción para recopilar información sobre la causa específica de la excepción.

Por ejemplo, el `CFileException` tipo tiene el `m_cause` miembro de datos, que contiene un tipo enumerado que especifica la causa de la excepción de archivo. Algunos ejemplos de los posibles valores devueltos son `CFileException::fileNotFound` y `CFileException::readOnly` .

En el ejemplo siguiente se muestra cómo examinar el contenido de un `CFileException` . Otros tipos de excepción se pueden examinar de forma similar.

[!code-cpp[NVC_MFCExceptions#13](codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

Para obtener más información, vea [excepciones: liberar objetos en excepciones](exceptions-freeing-objects-in-exceptions.md) y [excepciones: detectar y eliminar excepciones](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
