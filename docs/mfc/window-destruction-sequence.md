---
title: "Secuencia de destrucci&#243;n de ventanas | Microsoft Docs"
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
  - "objetos CWnd, secuencia de destrucción"
  - "destruir ventanas"
  - "destrucción, ventanas"
  - "secuencia [C++]"
  - "secuencia [C++], destrucción de ventana"
  - "ventanas [C++], destruir"
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Secuencia de destrucci&#243;n de ventanas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el marco de trabajo de MFC, cuando el usuario cierra la ventana de marco, el controlador predeterminado de [OnClose](../Topic/CWnd::OnClose.md) de la ventana llama [DestroyWindow](../Topic/CWnd::DestroyWindow.md).  La función del último miembro denominada cuando se destruye la ventana de Windows es [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md), que hace algún limpieza, llama a la función miembro de [valor predeterminado](../Topic/CWnd::Default.md) para realizar la limpieza de Windows, y llama a la función virtual [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)miembro.  La implementación de [CFrameWnd](../mfc/reference/cframewnd-class.md) de `PostNcDestroy` elimina el objeto de la ventana de C\+\+.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Asignando y desasignando memoria de la ventana](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Desasociar un CWnd del HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## Vea también  
 [Destruir objetos Window](../mfc/destroying-window-objects.md)