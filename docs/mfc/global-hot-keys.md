---
title: "Teclas de acceso directo globales | Microsoft Docs"
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
  - "CHotKeyCtrl (clase), teclas de acceso directo globales"
  - "teclas de acceso directo globales"
  - "métodos abreviados de teclado [C++], teclas de acceso rápido"
ms.assetid: e0b95d14-c571-4c9a-9cd1-e7fc1f0e278d
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Teclas de acceso directo globales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una tecla de acceso rápido global se asocia a una ventana determinada de nonchild.  Permite que el usuario active la ventana de cualquier parte del sistema.  Una aplicación establece una tecla de acceso rápido global para una ventana determinada enviando el mensaje de [WM\_SETHOTKEY](http://msdn.microsoft.com/library/windows/desktop/ms646284) a esa ventana.  Por ejemplo, si `m_HotKeyCtrl` es el objeto de [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md) y `pMainWnd` es un puntero a la ventana que se active cuando se presiona la tecla de acceso rápido, puede utilizar el código siguiente para asociar la tecla de acceso rápido especificada en el control con la ventana designada por a `pMainWnd`.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#18](../mfc/codesnippet/CPP/global-hot-keys_1.cpp)]  
  
 Siempre que el usuario presione una tecla de acceso rápido global, la ventana especificada recibe un mensaje de [WM\_SYSCOMMAND](http://msdn.microsoft.com/library/windows/desktop/ms646360) que especifique **SC\_HOTKEY** como el tipo de comando.  Este mensaje también provoca la ventana que se reciben.  Dado que este mensaje no incluye ninguna información en la clave exacta que se ha presionado, mediante este método no permite el distinguir entre distintas teclas de acceso rápido que se pueden adjuntar a la misma ventana.  La tecla de acceso rápido sigue siendo válida hasta la aplicación que sale **WM\_SETHOTKEY** enviado.  
  
## Vea también  
 [Usar CHotKeyCtrl](../mfc/using-chotkeyctrl.md)   
 [Controles](../mfc/controls-mfc.md)