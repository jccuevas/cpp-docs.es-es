---
title: "Funciones miembro del bot&#243;n de n&#250;mero | Microsoft Docs"
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
  - "CSpinButtonCtrl (clase), métodos"
  - "control de botón de número, métodos"
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones miembro del bot&#243;n de n&#250;mero
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay varias funciones miembro disponibles para el control de número \([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)\).  Utilice estas funciones para cambiar los atributos siguientes del botón de número.  
  
-   **Acceleration** puede ajustar la velocidad a la que la posición cambia cuando el usuario mantiene el botón de flecha.  Para ejecutar la aceleración, utilice [SetAccel](../Topic/CSpinButtonCtrl::SetAccel.md) y el miembro de [GetAccel](../Topic/CSpinButtonCtrl::GetAccel.md) funciona.  
  
-   **base** Puede cambiar base \(10 o 16\) utilizada para mostrar la posición de la leyenda de la ventana de relacionada.  Para ejecutar la base, utilice [GetBase](../Topic/CSpinButtonCtrl::GetBase.md) y el miembro de [SetBase](../Topic/CSpinButtonCtrl::SetBase.md) funciona.  
  
-   **Buddy Window** puede establecer dinámicamente la ventana de relacionada.  Para ver o cambiar que el control es la ventana de relacionada, utilice [GetBuddy](../Topic/CSpinButtonCtrl::GetBuddy.md) y el miembro de [SetBuddy](../Topic/CSpinButtonCtrl::SetBuddy.md) funciona.  
  
-   **Posición** Puede ver y cambiar su posición.  Para trabajar directamente con la posición, use [GetPos](../Topic/CSpinButtonCtrl::GetPos.md) y el miembro de [SetPos](../Topic/CSpinButtonCtrl::SetPos.md) funciona.  Puesto que la leyenda del control de relacionada puede haber cambiado \(por ejemplo, en caso de que el relacionada es un control de edición\), `GetPos` recupera la leyenda actual y contiene la posición en consecuencia.  
  
-   **Intervalo** Puede cambiar las posiciones máxima y mínimas para el botón de número.  De forma predeterminada, el máximo se establece en 0, y el mínimo se establece en 100.  Puesto que el valor máximo predeterminado es menor que el valor mínimo predeterminado, las acciones de los botones de flecha son contador\- intuitivos.  Normalmente, establecerá el intervalo utilizando la función miembro de [SetRange](../Topic/CSpinButtonCtrl::SetRange.md) .  Para ver el uso [GetRange](../Topic/CSpinButtonCtrl::GetRange.md)de intervalo.  
  
## Vea también  
 [Usar CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Controles](../mfc/controls-mfc.md)