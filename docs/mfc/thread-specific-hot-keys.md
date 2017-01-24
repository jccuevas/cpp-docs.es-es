---
title: "Teclas de acceso r&#225;pido espec&#237;ficas del subproceso | Microsoft Docs"
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
  - "teclas de acceso [C++], teclas de acceso rápido"
  - "CHotKeyCtrl (clase), teclas de acceso rápido específicas del subproceso"
  - "métodos abreviados de teclado [C++], teclas de acceso rápido"
  - "subprocesamiento [C++], teclas de acceso rápido en CHotKeyCtrl"
ms.assetid: b6021274-1498-483f-bcbf-ba5723547cc8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Teclas de acceso r&#225;pido espec&#237;ficas del subproceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una aplicación establece una tecla de acceso rápido subproceso\- concreta \([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)\) mediante la función de Windows **RegisterHotKey** .  Cuando el usuario presiona una tecla de acceso rápido subproceso\- específica, los elementos para exponer de Windows un mensaje de [WM\_HOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646279) al principio de la cola de subproceso determinado.  El mensaje de **WM\_HOTKEY** contiene el código de tecla virtual, el estado del cambio, y el identificador definido por el usuario de la tecla de acceso rápido concreta que se ha presionado.  Para obtener una lista de códigos de tecla virtual estándar, vea Winuser.h.  Para obtener más información sobre este método, vea [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
 Observe que los indicadores de estado de cambio utilizados en la llamada a **RegisterHotKey** no son iguales que los devueltos por la función miembro de [GetHotKey](../Topic/CHotKeyCtrl::GetHotKey.md) ; tendrá que convertir estos marcadores antes de llamar a **RegisterHotKey**.  
  
## Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)