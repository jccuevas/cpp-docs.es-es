---
title: "Ordenar elementos en el control de encabezado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DS_DRAGDROP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DS_DRAGDROP (notificación)"
  - "GetOrderArray (método)"
  - "controles del encabezado, ordenar elementos"
  - "OrderToIndex (método)"
  - "secuencia"
  - "secuencia, elementos de control de encabezado"
  - "SetOrderArray (método)"
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Ordenar elementos en el control de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una vez que se tiene [elementos agregados a un control de encabezado](../mfc/adding-items-to-the-header-control.md), puede manipular o recopilar información sobre el orden con las funciones siguientes:  
  
-   [CHeaderCtrl::GetOrderArray](../Topic/CHeaderCtrl::GetOrderArray.md) y [CHeaderCtrl::SetOrderArray](../Topic/CHeaderCtrl::SetOrderArray.md)  
  
     Obtiene y establece el orden de izquierda a derecha de los elementos de encabezado.  
  
-   [CHeaderCtrl::OrderToIndex](../Topic/CHeaderCtrl::OrderToIndex.md).  
  
     Recupera el valor de índice de un elemento concreto del encabezado.  
  
 Además de las funciones anteriores de miembro, el estilo de `HDS_DRAGDROP` permite al usuario arrastrar y colocar elementos de encabezado dentro del control de encabezado.  Para obtener más información, vea [Proporcionar compatibilidad de arrastrar y colocar para los elementos de encabezado](../mfc/providing-drag-and-drop-support-for-header-items.md).  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)