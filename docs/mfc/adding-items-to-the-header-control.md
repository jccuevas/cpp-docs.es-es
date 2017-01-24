---
title: "Agregar elementos al control de encabezado | Microsoft Docs"
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
  - "CHeaderCtrl (clase), agregar elementos"
  - "controles [MFC], encabezado"
  - "controles del encabezado, agregar elementos"
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar elementos al control de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Después de crear el control de encabezado \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) en la ventana primaria, agregue tantos “elementos de encabezado” como necesita: normalmente uno por columna.  
  
### Para agregar un elemento de encabezado  
  
1.  Preparar una estructura de [HD\_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) .  
  
2.  Llamada [CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md), pasando la estructura.  
  
3.  Repita los pasos 1 y 2 para los elementos adicionales.  
  
 Para obtener más información, vea [Agregar un elemento a un Control de encabezado](http://msdn.microsoft.com/library/windows/desktop/bb775238) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)