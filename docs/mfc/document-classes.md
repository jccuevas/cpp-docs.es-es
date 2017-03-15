---
title: "Clases de documento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.document"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases de documento"
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de documento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los objetos de la clase document, creados por los objetos de plantilla de documento, administran los datos de aplicación.  Se derivará una clase para los documentos desde una de estas clases.  
  
 Los objetos de la clase document interactúan con los objetos de vista.  Los objetos de vista representan el área cliente de una ventana, muestran datos de un documento, y permiten a los usuarios interactuar con él.  Documentos y vistas son creados por un objeto de plantilla de documento.  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 La clase base para los documentos específicos de la aplicación.  Derive la clase o clases de documento de **CDocument**.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Utilizado para la aplicación del documento compuesto, así como la compatibilidad básica del contenedor.  Actúa como contenedor para las clases derivadas de [CDocItem](../mfc/reference/cdocitem-class.md).  Esta clase se puede utilizar como clase base para los documentos contenedor y es la clase base para `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Una clase derivada de `COleDocument` que proporciona la infraestructura para vincular.  Debe derivar clases de documento para las aplicaciones contenedoras de esta clase en lugar de `COleDocument` si desea a admitir vínculos a objetos incrustados.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Mantiene la lista de elementos de OLE de cliente que están en el control rich edit.  Se utiliza con [CRichEditView](../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Se utiliza como clase base para las clases de documento de la aplicación de servidor.  los objetos de`COleServerDoc` proporcionan la mayor parte de compatibilidad de servidor mediante interacciones con los objetos de [COleServerItem](../mfc/reference/coleserveritem-class.md) .  La función de edición visual se proporciona mediante la arquitectura documento\/vista de la biblioteca de clases.  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 Asignación, [CHtmlEditView](../mfc/reference/chtmleditview-class.md), de la funcionalidad de la plataforma de edición HTML WebBrowser en el contexto de la arquitectura de la vista del documento de MFC.  
  
## Clases relacionadas  
 Los objetos de clase de documento pueden ser persistentes es decir pueden escribir su estado a un medio de almacenamiento y leer la reproducción.  MFC proporciona la clase de `CArchive` para facilitar la transferencia de datos del documento en un medio de almacenamiento.  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 Coopera con un objeto de [Archivo C](../mfc/reference/cfile-class.md) el almacenamiento persistente de implementan para los objetos con la serialización \(vea [CObject::Serialize](../Topic/CObject::Serialize.md)\).  
  
 Los documentos también pueden contener objetos OLE.  `CDocItem` es la clase base de los elementos del servidor y el cliente.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Clase base abstracta de [COleClientItem](../mfc/reference/coleclientitem-class.md) y de [COleServerItem](../mfc/reference/coleserveritem-class.md).  Los objetos de clases derivadas de `CDocItem` representan partes de documentos.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)