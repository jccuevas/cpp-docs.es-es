---
title: "Crear las listas de im&#225;genes | Microsoft Docs"
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
  - "CListCtrl (clase), crear las listas de imágenes para"
  - "listas de imágenes [C++], crear para CListCtrl"
  - "listas [C++], imagen"
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Crear las listas de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crear listas de imágenes es el mismo si utiliza [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md).  
  
> [!NOTE]
>  Solo necesita listas de imágenes si el control de lista incluye el estilo de `LVS_ICON` .  
  
 Clase `CImageList` de uso para crear una o más listas de imágenes \(para los iconos del mismo tamaño, pequeños iconos, y estados\).  Vea [CImageList](../mfc/reference/cimagelist-class.md), y vea [Listas de imágenes de la vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774736) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 Llamada [CListCtrl::SetImageList](../Topic/CListCtrl::SetImageList.md) para cada lista de imágenes; pase un puntero al objeto apropiado de `CImageList` .  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)