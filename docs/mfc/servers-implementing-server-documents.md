---
title: 'Servidores: Implementar documentos de servidor | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE server applications [MFC], managing server documents
- OLE server applications [MFC], implementing OLE servers
- servers, server documents
- server documents [MFC], implementing
ms.assetid: cca1451a-ad09-47ed-b56e-bccd78fc86d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 273fd1e5afefb8a10b3e1ae8e3c2f81ccec05e7f
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36950833"
---
# <a name="servers-implementing-server-documents"></a>Servidores: Implementar documentos de servidor
En este artículo se explica los pasos que debe seguir para implementar correctamente un documento de servidor si no se especificó la opción de servidor OLE en el Asistente para aplicaciones.  
  
#### <a name="to-define-a-server-document-class"></a>Para definir una clase de documento de servidor  
  
1.  Derive la clase de documento de `COleServerDoc` en lugar de `CDocument`.  
  
2.  Crear una clase de elemento de servidor derivada de `COleServerItem`.  
  
3.  Implemente el `OnGetEmbeddedItem` función de miembro de la clase de documento de servidor.  
  
     `OnGetEmbeddedItem` se llama cuando el usuario de una aplicación de contenedor crea o edita un elemento incrustado. Debe devolver un elemento que representa todo el documento. Debe ser un objeto de su `COleServerItem`-clase derivada.  
  
4.  Invalidar el `Serialize` función de miembro para serializar el contenido del documento. No es necesario serializar la lista de elementos del servidor a menos que esté usando para representar los datos nativos en el documento. Para obtener más información, consulte *implementar elementos de servidor* en el artículo [servidores: elementos de servidor](../mfc/servers-server-items.md).  
  
 Cuando se crea un documento de servidor, el marco de trabajo registra automáticamente el documento con la DLL del sistema OLE. Esto permite que los archivos DLL identificar los documentos de servidor.  
  
 Para obtener más información, consulte [COleServerItem](../mfc/reference/coleserveritem-class.md) y [COleServerDoc](../mfc/reference/coleserverdoc-class.md) en el *Class Library Reference*.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../mfc/servers.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)   
 [Servidores: Implementar un servidor](../mfc/servers-implementing-a-server.md)   
 [Servidores: Implementar ventanas de marco en contexto](../mfc/servers-implementing-in-place-frame-windows.md)

