---
title: "Desasociar CWnd de su HWND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "objetos CWnd, desasociar de HWND"
  - "método Detach (clase CWnd)"
  - "desasociar CWnd de HWND"
  - "HWND, desasociar CWnd de"
  - "quitar los HWND de CWnd"
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Desasociar CWnd de su HWND
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si necesita evitar la relación de`HWND` de objeto, MFC proporciona otra función miembro de `CWnd` , [Desasociar](../Topic/CWnd::Detach.md), que desconecta el objeto de la ventana de C\+\+ de la ventana de Windows.  Esto evita que el destructor destruya la ventana de Windows cuando se destruye el objeto.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Crear ventanas](../mfc/creating-windows.md)  
  
-   [Secuencia de destrucción ventana](../mfc/window-destruction-sequence.md)  
  
-   [Asignando y desasignando memoria de la ventana](../mfc/allocating-and-deallocating-window-memory.md)  
  
## Vea también  
 [Window \(Objetos\)](../mfc/window-objects.md)