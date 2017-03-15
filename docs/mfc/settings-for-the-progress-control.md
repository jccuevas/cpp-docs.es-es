---
title: "Configuraci&#243;n del control de progreso | Microsoft Docs"
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
  - "CProgressCtrl (clase), configuración"
  - "controles de progreso [C++], configuración"
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Configuraci&#243;n del control de progreso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La configuración básica del control de progreso \([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)\) son el intervalo y la posición actual.  El intervalo representa la duración completa de la operación.  La posición actual representa el progreso que la aplicación ha creado para completar la operación.  Los cambios al intervalo o la causa de la posición el control de progreso de actualizarse.  
  
 De forma predeterminada, se establece en 0 – 100, y la posición inicial se establece en 0.  Para recuperar los valores actuales del intervalo para el control de progreso, utilice la función miembro de [GetRange](../Topic/CProgressCtrl::GetRange.md) .  Para cambiar el intervalo, utilice la función miembro de [SetRange](../Topic/CProgressCtrl::SetRange.md) .  
  
 Para establecer la posición, use [SetPos](../Topic/CProgressCtrl::SetPos.md).  Para recuperar la posición actual sin especificar un nuevo valor, utilice [GetPos](../Topic/CProgressCtrl::GetPos.md).  Por ejemplo, quizás desee ver simplemente en el estado de la operación actual.  
  
 Para ver la posición actual del control de progreso, utilice [StepIt](../Topic/CProgressCtrl::StepIt.md).  Para establecer la cantidad de cada paso, utilice [SetStep](../Topic/CProgressCtrl::SetStep.md)  
  
## Vea también  
 [Usar CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Controles](../mfc/controls-mfc.md)