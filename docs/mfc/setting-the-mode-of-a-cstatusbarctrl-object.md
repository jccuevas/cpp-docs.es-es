---
title: "Establecer el modo de un objeto CStatusBarCtrl | Microsoft Docs"
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
  - "CStatusBarCtrl (clase), modos simples y no simples"
  - "IsSimple (método), utilizar"
  - "modo no simple y controles de la barra de estado"
  - "SetSimple (método)"
  - "modo simple y controles de la barra de estado"
  - "controles de la barra de estado, modos simples y no simples"
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Establecer el modo de un objeto CStatusBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay dos modos para un objeto de `CStatusBarCtrl` : simple y nonsimple.  En la mayoría de casos, el control de barra de estado tendrá uno o varios elementos, junto con el texto y quizás un icono o iconos.  Esto es el modo de nonsimple.  Para obtener más información sobre este modo, vea [Inicializar la Parte de un objeto de CStatusBarCtrl](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md).  
  
 Sin embargo, hay casos donde sólo es necesario mostrar una línea de texto única.  En este caso, el modo simple es suficiente para necesidades.  Para cambiar el modo del objeto de `CStatusBarCtrl` a simple, haga una llamada a la función miembro de [SetSimple](../Topic/CStatusBarCtrl::SetSimple.md) .  Una vez que el control de barra de estado está en modo simple, establezca el texto llamando a la función miembro de **SetText** , pasando 255 como valor para el parámetro de **nPane** .  
  
 Puede utilizar la función de [IsSimple](../Topic/CStatusBarCtrl::IsSimple.md) para determinar en qué modo es el objeto de `CStatusBarCtrl` .  
  
> [!NOTE]
>  Si el objeto de la barra de estado se cambia de nonsimple a simple, o viceversa, la ventana inmediatamente está rediseñada y, si es necesario, cualquier elemento definido automáticamente se restaura.  
  
## Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)