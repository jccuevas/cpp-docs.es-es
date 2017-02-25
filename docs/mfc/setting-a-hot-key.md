---
title: "Establecer una tecla de acceso r&#225;pido | Microsoft Docs"
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
  - "teclas de acceso [C++], teclas de acceso rápido"
  - "CHotKeyCtrl (clase), establecer tecla de acceso rápido"
  - "métodos abreviados de teclado [C++], teclas de acceso rápido"
ms.assetid: 6f3bc141-e346-4dce-9ca7-3e6b2c453f3f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Establecer una tecla de acceso r&#225;pido
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La aplicación puede utilizar la información proporcionada por un control de la tecla de acceso rápido \([CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md)\) de dos maneras:  
  
-   Configurar una tecla de acceso rápido global para activar una ventana de nonchild enviando un mensaje de [WM\_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) a la ventana que se va a activar.  
  
-   Configurar una tecla de acceso rápido subproceso\- concreta llamando a la función de Windows [RegisterHotKey](http://msdn.microsoft.com/library/windows/desktop/ms646309).  
  
## Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)