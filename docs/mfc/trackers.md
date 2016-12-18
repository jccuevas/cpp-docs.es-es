---
title: "Seguimiento | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aplicaciones [OLE], seguimiento"
  - "CDC (clase), seguimiento"
  - "CRectTracker (clase), implementar seguimiento"
  - "aplicaciones OLE [C++], seguimiento"
  - "contenedores OLE, seguimiento"
  - "aplicaciones de servidor OLE, seguimiento"
  - "seguimiento"
  - "seguimiento de elementos OLE"
ms.assetid: dcd09399-6637-4621-80e5-d12670429787
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Seguimiento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de [CRectTracker](../mfc/reference/crecttracker-class.md) proporciona una interfaz de usuario entre los elementos rectangulares en la aplicación y el usuario proporcionando una variedad de estilos de presentación.  Estos estilos incluyen sólido, tramado, o los bordes de línea discontinua; un modelo tramado que cubre el elemento; y controladores de cambio de tamaño que pueden encontrarse fuera o dentro de un borde.  Los rastreadores suelen utilizarse junto con los elementos de OLE, es decir, objetos derivados de `COleClientItem`.  Los rectángulos de seguimiento proporcionan indicaciones visuales en el estado actual del elemento.  
  
 El ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md) de MFC ilustra una interfaz común mediante los rastreadores y elementos de OLE del cliente desde el punto de vista de aplicación contenedora.  Para obtener una demostración de distintos estilos y capacidades de un objeto de seguimiento, vea a MFC el ejemplo general [RASTREADOR](../top/visual-cpp-samples.md).  
  
 Para obtener más información sobre cómo implementar los rastreadores en la aplicación OLE, vea [Rastreadores: Implementar los rastreadores en la aplicación OLE de The](../mfc/trackers-implementing-trackers-in-your-ole-application.md)  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [COleClientItem Class](../mfc/reference/coleclientitem-class.md)