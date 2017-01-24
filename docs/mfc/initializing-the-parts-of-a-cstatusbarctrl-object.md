---
title: "Inicializar los elementos de un objeto CStatusBarCtrl | Microsoft Docs"
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
  - "CStatusBarCtrl (clase), declarar partes de"
  - "CStatusBarCtrl (clase), modo simple"
  - "iconos, utilizar en barras de estado"
  - "barras de estado simples"
  - "barras de estado, declarar partes de"
  - "barras de estado, iconos"
  - "barras de estado, modo simple"
ms.assetid: 60e8f285-d2d8-424a-a6ea-2fc548370303
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Inicializar los elementos de un objeto CStatusBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, una barra de estado muestra la información de estado en los paneles independientes.  Estos paneles \(también denominados elementos\) pueden contener una cadena de texto, el icono, o ambas.  
  
 Utilice [SetParts](../Topic/CStatusBarCtrl::SetParts.md) para definir cuántas partes, y la longitud, tendrá la barra de estado.  Después de haber creado las partes de la barra de estado, haga las llamadas a [SetText](../Topic/CStatusBarCtrl::SetText.md) y a [SetIcon](../Topic/CStatusBarCtrl::SetIcon.md) para establecer el texto o el icono de una parte específica de la barra de estado.  Una vez que el elemento se ha establecido correctamente, el control automáticamente se dibuje de nuevo.  
  
 El ejemplo siguiente se inicializa un objeto existente de `CStatusBarCtrl` \(`m_StatusBarCtrl`\) con cuatro paneles y establezca un icono \(IDI\_I CON1\) y texto en la segunda partición.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#31](../mfc/codesnippet/CPP/initializing-the-parts-of-a-cstatusbarctrl-object_1.cpp)]  
  
 Para obtener más información sobre cómo establecer el modo de un objeto de `CStatusBarCtrl` a simple, vea [Establecer el modo de un objeto de CStatusBarCtrl](../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).  
  
## Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)