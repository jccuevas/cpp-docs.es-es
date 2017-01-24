---
title: "Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl (clase), crear"
  - "controles de la barra de estado, crear"
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A continuación se muestra un ejemplo típico de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):  
  
### Para utilizar un control de barra de estado con elementos  
  
1.  Cree el objeto de `CStatusBarCtrl` .  
  
2.  Llame a [SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md) si desea establecer el alto mínimo del área de dibujo del control de barra de estado.  
  
3.  Llame a [SetBkColor](../Topic/CStatusBarCtrl::SetBkColor.md) para establecer el color de fondo del control de barra de estado.  
  
4.  Llamada [SetParts](../Topic/CStatusBarCtrl::SetParts.md) para establecer el número de elementos en un control de barra de estado y la coordenada del borde derecho de cada partición.  
  
5.  Llame a [SetText](../Topic/CStatusBarCtrl::SetText.md) para establecer el texto en una parte determinada del control de barra de estado.  El mensaje invalida la parte del control que ha cambiado, haciendo que muestra el nuevo texto cuando el control después recibe el mensaje de `WM_PAINT` .  
  
 En algunos casos, la barra de estado sólo necesita mostrar una línea de texto.  En este caso, haga una llamada a [SetSimple](../Topic/CStatusBarCtrl::SetSimple.md).  Esto coloca el control de barra de estado en modo “simple”, que muestra una línea de texto única.  
  
## Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)