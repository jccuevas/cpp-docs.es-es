---
title: "Clases de contenedor OLE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX (clases) [C++]"
  - "clases de contenedor [C++]"
  - "contenedores [C++], aplicaciones de contenedor OLE"
  - "OLE [C++], clases"
  - "clases OLE [C++]"
  - "edición visual [C++], clases"
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de contenedor OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases se utilizan en aplicaciones contenedoras.  `COleLinkingDoc` y `COleDocument` administran colecciones de objetos de `COleClientItem` .  En lugar de derivar la clase de **CDocument**, se derivará de `COleLinkingDoc` o de `COleDocument`, según se desee compatibilidad para los vínculos a objetos incrustados en el documento.  
  
 Utilice un objeto de `COleClientItem` para representar cada elemento OLE en el documento que se inserta de otro documento o es un vínculo a otro documento.  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 Admite la contención del documento activo.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Utilizado para la aplicación del documento compuesto, así como la compatibilidad básica del contenedor.  Actúa como contenedor para las clases derivadas de `CDocItem`.  Esta clase se puede utilizar como clase base para los documentos contenedor y es la clase base para `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Una clase derivada de `COleDocument` que proporciona la infraestructura para vincular.  Debe derivar clases de documento para las aplicaciones contenedoras de esta clase en lugar de `COleDocument` si desea a admitir vínculos a objetos incrustados.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Mantiene la lista de elementos de OLE de cliente que están en el control rich edit.  Se utiliza con [CRichEditView](../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Clase base abstracta de `COleClientItem` y de `COleServerItem`.  Los objetos de clases derivadas de `CDocItem` representan partes de documentos.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 Una clase de elemento customer que representa el cliente de la conexión a un elemento OLE incrustado o vinculado.  Derive los elementos de cliente de esta clase.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Proporciona acceso de cliente a un elemento OLE almacenado en un control rich edit cuando se utiliza con `CRichEditView` y `CRichEditDoc`.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Una excepción resultando de un error en el procesamiento OLE.  Esta clase es utilizada por los contenedores y servidores.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)