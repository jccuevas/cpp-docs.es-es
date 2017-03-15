---
title: "M&#233;todos de creaci&#243;n de una barra de estado | Microsoft Docs"
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
  - "CStatusBar (clase), frente a CStatusBarCtrl"
  - "CStatusBarCtrl (clase), crear"
  - "CStatusBarCtrl (clase), frente a CStatusBar"
  - "métodos [MFC]"
  - "métodos [MFC], crear barras de estado"
  - "barras de estado, crear"
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# M&#233;todos de creaci&#243;n de una barra de estado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC proporciona dos clases para crear barras de estado: [CStatusBar](../mfc/reference/cstatusbar-class.md) y [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) \(que contiene el control común API de Windows\).  `CStatusBar` proporciona toda la funcionalidad de controles comunes de la barra de estado, automáticamente interactúa con los menús y barras de herramientas, y controla muchos de los valores necesarios y estructuras de control común para se; sin embargo, el archivo ejecutable resultante será normalmente mayor que lo creó mediante `CStatusBarCtrl`.  
  
 `CStatusBarCtrl` produce normalmente a un ejecutable menor, y puede optar por utilizar `CStatusBarCtrl` si no piensa integrar la barra de estado en la arquitectura de MFC.  Si piensa utilizar `CStatusBarCtrl` y para integrar la barra de estado en la arquitectura de MFC, debe tener cuidado adicional para comunicar manipulaciones del control de barra de estado a MFC.  Esta comunicación no es difícil; sin embargo, es el trabajo adicional que no es necesario cuando se utiliza `CStatusBar`.  
  
 Visual C\+\+ proporciona dos maneras de aprovechar el control común de la barra de estado.  
  
-   Cree la barra de estado mediante `CStatusBar`, y llame a [CStatusBar::GetStatusBarCtrl](../Topic/CStatusBar::GetStatusBarCtrl.md) para obtener acceso a las funciones miembro de `CStatusBarCtrl` .  
  
-   Cree la barra de estado mediante el constructor de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) .  
  
 Cualquier método dará el acceso a las funciones miembro del control de barra de estado.  Cuando se llama a `CStatusBar::GetStatusBarCtrl`, devuelve una referencia a un objeto de `CStatusBarCtrl` para poder utilizar alguna establece de funciones miembro.  Vea [CStatusBar](../mfc/reference/cstatusbar-class.md) para obtener información sobre la construcción y crear una barra de estado mediante `CStatusBar`.  
  
## Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)