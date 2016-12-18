---
title: "Comunicar con un control de &#225;rbol | Microsoft Docs"
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
  - "comunicaciones, controles de árbol"
  - "CTreeCtrl (clase), llamar a funciones miembro"
  - "controles de árbol"
  - "controles de árbol, comunicar con"
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Comunicar con un control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Utilice los distintos métodos para llamar a funciones miembro de un objeto de [CTreeCtrl](../mfc/reference/ctreectrl-class.md) dependiendo de cómo se creó el objeto:  
  
-   Si el control de árbol está en un cuadro de diálogo, utilice una variable miembro de `CTreeCtrl` con el que se crea en la clase del cuadro de diálogo.  
  
-   Si el control de árbol es una ventana secundaria, utilice el objeto de `CTreeCtrl` \(o el puntero\) que se construía el objeto.  
  
-   Si está utilizando un objeto de `CTreeView` , utilice la función [CTreeView::GetTreeCtrl](../Topic/CTreeView::GetTreeCtrl.md) para obtener una referencia al control de árbol.  Puede inicializar otra referencia con este valor o asignar la dirección de la referencia a un puntero de `CTreeCtrl` .  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)