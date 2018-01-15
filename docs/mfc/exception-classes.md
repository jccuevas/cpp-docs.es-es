---
title: "Clases de excepción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.exception
dev_langs: C++
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b848cf1a839940925222a50ce016ba91da4d371d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exception-classes"></a>Clases de excepciones
La biblioteca de clases proporciona un mecanismo de control de excepciones basado en clase `CException`. El marco de aplicación usa las excepciones en su código; También puede usar en el suyo. Para obtener más información, vea el artículo [excepciones](../mfc/exception-handling-in-mfc.md). Puede derivar sus propios tipos de excepción desde `CException`.  
  
 MFC proporciona una clase de excepción de la que puede derivar su propia excepción, así como clases de excepción para todas las excepciones que admite.  
  
 [CException](../mfc/reference/cexception-class.md)  
 La clase base de las excepciones.  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Una excepción de archivo.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Una excepción resultante de un error en una operación de base de datos DAO.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Una excepción resultante de un error en el procesamiento de la base de datos ODBC.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Una excepción orientada a servicios de archivo.  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 Una excepción de memoria insuficiente.  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 Una excepción resultante de usar una característica no compatible.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Una excepción resultante de un error en el procesamiento de OLE. Esta clase se utiliza por contenedores y servidores.  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 Una excepción resultante de un error durante la automatización. Excepciones de automatización son iniciadas por servidores de automatización y detecta los clientes de automatización.  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 Una excepción resultante de un error al cargar un recurso de Windows.  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 Una excepción que se usa para detener una operación iniciada por el usuario. Normalmente, el usuario ha notificado el problema antes de que se produce esta excepción.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

