---
title: "Usar informaciones sobre herramientas en un objeto CStatusBarCtrl | Microsoft Docs"
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
  - "CStatusBarCtrl (clase), información sobre herramientas"
  - "barras de estado, información sobre herramientas"
  - "información sobre herramientas [C++], utilizar en barras de estado"
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar informaciones sobre herramientas en un objeto CStatusBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para habilitar la información sobre herramientas para un control de barra de estado, cree el objeto de `CStatusBarCtrl` con el estilo de **SBT\_TOOLTIPS** .  
  
> [!NOTE]
>  Si está utilizando un objeto de `CStatusBar` para implementar la barra de estado, use la función de `CStatusBar::CreateEx` .  Permite especificar los estilos adicionales para el objeto incrustado de **CStatusBarCtrl** .  
  
 Una vez que el objeto de `CStatusBarCtrl` se ha creado correctamente, utilice [CStatusBarCtrl::SetTipText](../Topic/CStatusBarCtrl::SetTipText.md) y [CStatusBarCtrl::GetTipText](../Topic/CStatusBarCtrl::GetTipText.md) de establecer y recuperar el texto de sugerencia para un panel concreto.  
  
 Una vez que se ha establecido la información sobre herramientas, solo se muestra si el elemento tiene un icono y ningún texto, o si todo el texto no se pueden mostrar dentro del elemento.  La información sobre herramientas no se admiten en modo simple.  
  
## Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)