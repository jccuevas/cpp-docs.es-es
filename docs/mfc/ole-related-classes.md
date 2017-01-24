---
title: "Clases relacionadas con OLE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
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
  - "OLE [C++], clases"
  - "clases OLE [C++]"
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases relacionadas con OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases proporcionan varios servicios, extendiéndose de excepciones a la entrada y la salida del archivo.  
  
 [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)  
 Se utiliza para crear elementos cuando se solicita de otros contenedores.  Esta clase actúa como clase base para los tipos más específicos de generadores, incluidos `COleTemplateServer`.  
  
 [COleMessageFilter](../mfc/reference/colemessagefilter-class.md)  
 Se utiliza para administrar la simultaneidad con las Llamadas a procedimiento remoto \(LRPC\) OLE Lightweight.  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Utiliza la interfaz COM de `IStream` para proporcionar acceso de `CFile` a archivos compuestos.  Esta clase \(derivada de `CFile`\) permite que la serialización de MFC para utilizar almacenamiento estructurado OLE.  
  
 [CRectTracker](../mfc/reference/crecttracker-class.md)  
 Utilizado para permitir mover, cambiar de tamaño, y la reorientación de elementos de contexto.  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)