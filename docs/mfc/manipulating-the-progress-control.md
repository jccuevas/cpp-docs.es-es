---
title: "Manipular el control de progreso | Microsoft Docs"
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
  - "controlar controles de progreso"
  - "CProgressCtrl (clase), manipular"
  - "CProgressCtrl (clase), utilizar"
  - "CProgressCtrl (clase), trabajar con"
  - "controles de progreso [C++], manipular"
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Manipular el control de progreso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay tres maneras de cambiar la posición actual de un control de progreso \([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)\).  
  
-   La posición se puede cambiar en una cantidad preestablecidos de incremento.  
  
-   La posición se puede cambiar en una cantidad arbitrario.  
  
-   La posición se puede cambiar a un valor concreto.  
  
### Para cambiar la posición en una cantidad preestablecidos  
  
1.  Utilice la función miembro de [SetStep](../Topic/CProgressCtrl::SetStep.md) para establecer la cantidad de incremento.  El valor predeterminado es 10.  Este valor se establece normalmente como una de las configuraciones iniciales para el control.  El valor de incremento puede ser negativo.  
  
2.  Utilice la función miembro de [StepIt](../Topic/CProgressCtrl::StepIt.md) para aumentar la posición.  Esto hace que el control para actualizarse.  
  
    > [!NOTE]
    >  `StepIt` hará que la posición de ajuste.  Por ejemplo, dado un intervalo de 1 a 100, un paso de 20, y una posición de 90, `StepIt` establecen la posición en 10.  
  
### Para cambiar la posición en una cantidad arbitrario  
  
1.  Utilice la función miembro de [OffsetPos](../Topic/CProgressCtrl::OffsetPos.md) para cambiar la posición.  `OffsetPos` aceptará valores negativos.  
  
    > [!NOTE]
    >  `OffsetPos`, a diferencia de `StepIt`, no se ajustará la posición.  La nueva posición se ajusta para permanecer dentro del intervalo.  
  
### Para cambiar la posición en un valor concreto  
  
1.  Utilice la función miembro de [SetPos](../Topic/CProgressCtrl::SetPos.md) para establecer la posición en un valor concreto.  En caso necesario, la nueva posición se ajusta para ser dentro del intervalo.  
  
 Normalmente, el control de progreso se utiliza para la salida.  Para obtener la posición actual sin especificar un nuevo valor, utilice [GetPos](../Topic/CProgressCtrl::GetPos.md).  
  
## Vea también  
 [Usar CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Controles](../mfc/controls-mfc.md)