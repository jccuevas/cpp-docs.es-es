---
title: "Servidores: Implementar documentos de servidor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones de servidor OLE, implementar servidores OLE"
  - "aplicaciones de servidor OLE, administrar documentos de servidor"
  - "documentos de servidor, implementar"
  - "servidores, documentos de servidor"
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Servidores: Implementar documentos de servidor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica los pasos que debe seguir para implementar correctamente un documento de servidor si no ha especificado la opción de servidor OLE en el asistente para aplicaciones.  
  
#### Para definir una clase de documento del servidor  
  
1.  Derive la clase de `COleServerDoc` en lugar de **CDocument**.  
  
2.  Cree una clase de elemento de servidor derivada de `COleServerItem`.  
  
3.  Implemente la función miembro de `OnGetEmbeddedItem` de la clase de documento del servidor.  
  
     se llama`OnGetEmbeddedItem` cuando el usuario de una aplicación contenedora crea o modifica un elemento incrustado.  Debe devolver un elemento que representa el documento.  Debería ser un objeto de `COleServerItem`\- clase derivada.  
  
4.  Reemplace la función miembro de `Serialize` para serializar el contenido del documento.  No es necesario serializar la lista de elementos del servidor a menos que se utiliza para representar datos nativos en el documento.  Para obtener más información, vea *implementar elementos del Servidor* en el caso [Servidores: Elementos de Servidor](../mfc/servers-server-items.md).  
  
 Cuando se crea un documento de servidor, el marco registra automáticamente el documento con los archivos DLL de OLE del sistema.  Esto permite que los archivos DLL identifican los documentos de servidor.  
  
 Para obtener más información, vea [COleServerItem](../mfc/reference/coleserveritem-class.md) y [COleServerDoc](../mfc/reference/coleserverdoc-class.md) en *la referencia de la biblioteca de clases*.  
  
## Vea también  
 [Servidores](../mfc/servers.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)   
 [Servidores: Implementar un servidor](../mfc/servers-implementing-a-server.md)   
 [Servidores: Implementar ventanas de marco en contexto](../mfc/servers-implementing-in-place-frame-windows.md)