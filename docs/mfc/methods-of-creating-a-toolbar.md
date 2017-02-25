---
title: "M&#233;todos de creaci&#243;n de una barra de herramientas | Microsoft Docs"
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
  - "CToolBar (clase), crear barras de herramientas"
  - "CToolBarCtrl (clase), y CToolBar (clase)"
  - "CToolBarCtrl (clase), crear barras de herramientas"
  - "barras de herramientas de MFC"
  - "controles de barra de herramientas [MFC]"
  - "controles de barra de herramientas [MFC], crear"
ms.assetid: f19d8d65-d49f-445c-abe8-d47d3e4101c8
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# M&#233;todos de creaci&#243;n de una barra de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC proporciona dos clases para crear barras de herramientas: [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) \(que contiene el control común API de Windows\).  `CToolBar` proporciona toda la funcionalidad de controles comunes de la barra de herramientas, y controla muchos de los valores necesarios y estructuras de control común para se; sin embargo, el archivo ejecutable resultante será normalmente mayor que lo creó mediante `CToolBarCtrl`.  
  
 `CToolBarCtrl` produce normalmente a un ejecutable menor, y puede optar por utilizar `CToolBarCtrl` si no piensa integrar la barra de herramientas de la arquitectura de MFC.  Si piensa utilizar `CToolBarCtrl` y para integrar la barra de herramientas de la arquitectura de MFC, debe tener cuidado adicional para comunicar manipulaciones de control toolbar a MFC.  Esta comunicación no es difícil; sin embargo, es el trabajo adicional que no es necesario cuando se utiliza `CToolBar`.  
  
 Visual C\+\+ proporciona dos maneras de aprovechar el control común de la barra de herramientas.  
  
-   Cree la barra de herramientas mediante `CToolBar`, y llame a [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md) para obtener acceso a las funciones miembro de `CToolBarCtrl` .  
  
-   Cree la barra de herramientas mediante el constructor de [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .  
  
 Cualquier método dará el acceso a las funciones miembro de control toolbar.  Cuando se llama a `CToolBar::GetToolBarCtrl`, devuelve una referencia a un objeto de `CToolBarCtrl` para poder utilizar alguna establece de funciones miembro.  Vea [CToolBar](../mfc/reference/ctoolbar-class.md) para obtener información sobre la construcción y crear una barra de herramientas mediante `CToolBar`.  
  
## Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)