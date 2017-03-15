---
title: "Clases de servidor OLE | Microsoft Docs"
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
  - "componentes COM, clases"
  - "clases de componentes"
  - "aplicaciones de servidor OLE, clases de servidor"
  - "documentos de servidor OLE"
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Clases de servidor OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases se utilizan en aplicaciones de servidor.  Los documentos de Servidor se derivan de `COleServerDoc` en lugar de **CDocument**.  Dado que `COleServerDoc` se deriva de `COleLinkingDoc`, documentos de servidor también pueden ser contenedores que admiten vínculos.  
  
 La clase de `COleServerItem` representa un documento o una parte de un documento al que pueda insertarlos en otro documento o vincular.  
  
 `COleIPFrameWnd` y `COleResizeBar` admiten la edición en contexto mientras el objeto está en un contenedor, y `COleTemplateServer` admite la creación de objetos de documento y vista para que los objetos OLE de otras aplicaciones pueden editar.  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Se utiliza como clase base para las clases de documento de la aplicación de servidor.  los objetos de`COleServerDoc` proporcionan la mayor parte de compatibilidad de servidor mediante interacciones con los objetos de `COleServerItem` .  La función de edición visual se proporciona mediante la arquitectura documento\/vista de la biblioteca de clases.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Clase base abstracta de `COleClientItem` y de `COleServerItem`.  Los objetos de clases derivadas de `CDocItem` representan partes de documentos.  
  
 [COleServerItem](../mfc/reference/coleserveritem-class.md)  
 Se utiliza para representar la interfaz\) a los elementos de `COleServerDoc` .  Hay normalmente un objeto de `COleServerDoc` , que representa la parte incrustada de un documento.  En los servidores que admitir vínculos partes de documentos, que pueden ser muchos objetos de `COleServerItem` , que representa un vínculo a un elemento.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Proporciona la ventana cuadro de una vista a un documento de servidor se edita en contexto.  
  
 [COleResizeBar](../mfc/reference/coleresizebar-class.md)  
 Proporciona la interfaz de usuario estándar para cambiar el tamaño en contexto.  Los objetos de este tipo siempre se utilizan junto con los objetos de `COleIPFrameWnd` .  
  
 [COleTemplateServer](../mfc/reference/coletemplateserver-class.md)  
 Utilizado para crear documentos con la arquitectura documento\/vista del marco.  Un objeto de `COleTemplateServer` delega la mayoría del trabajo a un objeto asociado de `CDocTemplate` .  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Una excepción resultando de un error en el procesamiento OLE.  Esta clase es utilizada por los contenedores y servidores.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)