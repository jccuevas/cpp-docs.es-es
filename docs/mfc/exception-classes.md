---
title: "Clases de excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.exception"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de excepciones"
  - "control de excepciones, clases de excepciones"
  - "MFC, excepciones"
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clases de excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La biblioteca de clases proporciona un mecanismo excepción\-que administra basado en la clase `CException`.  El marco de aplicación usa las excepciones en el código; también puede utilizarlos en thes.  Para obtener más información, vea el artículo [Excepciones](../mfc/exception-handling-in-mfc.md).  Puede derivar dispone de tipos de excepción de `CException`.  
  
 MFC proporciona una clase de excepción que se puede derivar dispone la excepción así como las clases de excepción para todas las excepciones que admite.  
  
 [CException](../mfc/reference/cexception-class.md)  
 La clase base para las excepciones.  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Una excepción del archivo.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Una excepción resultando de un error en una operación de base de datos de DAO.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Una excepción resultando de un error en el procesamiento de la base de datos ODBC.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Una excepción orientada al archivo.  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 Una excepción de hacia fuera\-de\-memoria.  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 Una excepción resultando de utilizar una característica no compatible.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Una excepción resultando de un error en el procesamiento OLE.  Esta clase es utilizada por los contenedores y servidores.  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 Una excepción resultando de un error durante la automatización.  Las excepciones de automatización producen los servidores de automatización y detectadas por los clientes de automatización.  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 Una excepción resultando de un error cargar un recurso de Windows.  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 Una excepción utilizada para detener una operación usuario\-iniciada.  Normalmente, se han notificado al usuario del problema antes de que se produzca esta excepción.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)