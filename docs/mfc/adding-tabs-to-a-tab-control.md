---
title: "Agregar pesta&#241;as a un control de pesta&#241;a | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CTabCtrl (clase), agregar pestañas"
  - "poner pestañas en CTabCtrls"
  - "controles de fichas, agregar pestañas"
  - "pestañas, agregar a la clase CTabCtrl"
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar pesta&#241;as a un control de pesta&#241;a
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Después de crear el control de ficha \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\), agregue tantas fichas como necesite.  
  
### Para agregar un elemento de fichas  
  
1.  Preparar una estructura de [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) .  
  
2.  Llamada [CTabCtrl::InsertItem](../Topic/CTabCtrl::InsertItem.md), pasando la estructura.  
  
3.  Repita los pasos 1 y 2 para los elementos adicionales de la pestaña.  
  
 Para obtener más información, vea [Crear un Control tab](http://msdn.microsoft.com/library/windows/desktop/bb760550) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CTabCtrl](../mfc/using-ctabctrl.md)   
 [Controles](../mfc/controls-mfc.md)