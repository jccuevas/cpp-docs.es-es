---
title: "Efecto de banda el&#225;stica y seguimiento | Microsoft Docs"
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
  - "CRectTracker (clase), implementar seguimiento"
  - "objetos OLE, seleccionar"
  - "banda elástica"
  - "seguimiento"
  - "WM_LBUTTONDOWN"
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Efecto de banda el&#225;stica y seguimiento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Otra característica proporcionada con los rastreadores es la selección de “caucho\- banda”, que permite a un usuario a varios elementos seleccionar OLE arrastrando un rectángulo de tamaño alrededor de los elementos que se seleccionen.  Cuando el usuario suelta el botón primario, elementos dentro de la región seleccionada por el usuario se selecciona y pueden ser manipulados por el usuario.  Por ejemplo, el usuario puede arrastrar la selección en otra aplicación contenedora.  
  
 Implementar esta característica requiere algún código adicional en la función de controlador de `WM_LBUTTONDOWN` de la aplicación.  
  
 El ejemplo de código siguiente implementa la selección de la caucho\-banda y características adicionales.  
  
 [!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/CPP/rubber-banding-and-trackers_1.cpp)]  
  
 Si desea permitir la guía reversible de seguimiento durante el efecto de banda elástica, debe llamar a [CRectTracker::TrackRubberBand](../Topic/CRectTracker::TrackRubberBand.md) con el tercer parámetro establecido en **VERDADERO**.  Recuerde que permitir la guía reversible hará a veces [CRectTracker::m\_rect](../Topic/CRectTracker::m_rect.md) para invertirse.  Esto se puede corregir por una llamada a [CRect::NormalizeRect](../Topic/CRect::NormalizeRect.md).  
  
 Para obtener más información, vea [Elementos del contenedor](../mfc/containers-client-items.md) y [Personalizar arrastrar y colocar](../mfc/drag-and-drop-customizing.md).  
  
## Vea también  
 [Seguimiento: Implementar el seguimiento en la aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)   
 [CRectTracker Class](../mfc/reference/crecttracker-class.md)