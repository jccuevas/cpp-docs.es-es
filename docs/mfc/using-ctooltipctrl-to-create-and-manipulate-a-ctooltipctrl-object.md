---
title: "Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CToolTipCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolTipCtrl (clase), utilizar"
  - "información sobre herramientas [C++], crear"
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A continuación se muestra un ejemplo de uso de [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) :  
  
### Para crear y manipular un CToolTipCtrl  
  
1.  Cree el objeto de `CToolTipCtrl` .  
  
2.  Llame a [crear](../Topic/CToolTipCtrl::Create.md) para crear el control común de información sobre herramientas de Windows y para adjuntarlo al objeto de `CToolTipCtrl` .  
  
3.  Llamada [AddTool](../Topic/CToolTipCtrl::AddTool.md) para registrar una herramienta en el control de información sobre herramientas, para mostrar la información almacenada en la información sobre herramientas cuando el cursor está en la herramienta.  
  
4.  Llame a [SetToolInfo](../Topic/CToolTipCtrl::SetToolInfo.md) para establecer la información que una información sobre herramientas mantiene de herramienta.  
  
5.  Llame a [SetToolRect](../Topic/CToolTipCtrl::SetToolRect.md) para establecer un nuevo rectángulo delimitador para la herramienta.  
  
6.  Llame a [HitTest](../Topic/CToolTipCtrl::HitTest.md) para probar un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada y, si es así recuperar información acerca de la herramienta.  
  
7.  Llame a [GetToolCount](../Topic/CToolTipCtrl::GetToolCount.md) para recuperar un recuento de las herramientas registran con el control de información sobre herramientas.  
  
## Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)