---
title: "Destruir objetos Window | Microsoft Docs"
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
  - "ventanas de marco, destruir"
  - "Window (objetos), eliminar"
  - "Window (objetos), destruir"
  - "Window (objetos), quitar"
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Destruir objetos Window
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se debe tener cuidado con dispone de las ventanas secundarias para destruir el objeto de la ventana de C\+\+ cuando el usuario ha finalizado con la ventana.  Si estos objetos no se destruyen, la aplicación no se recuperará su memoria.  Afortunadamente, el marco administra la destrucción así como la creación de la ventana para las ventanas de marco, vistas, y los cuadros de diálogo.  Si crea ventanas adicionales, es responsable de destruirlas.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Secuencia de destrucción ventana](../mfc/window-destruction-sequence.md)  
  
-   [Asignando y desasignando memoria de la ventana](../mfc/allocating-and-deallocating-window-memory.md)  
  
-   [Desasociar un CWnd del HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Flujo general de creación de la ventana](../mfc/general-window-creation-sequence.md)  
  
-   [Ventanas de destrucción de cuadro](../mfc/destroying-frame-windows.md)  
  
## Vea también  
 [Window \(Objetos\)](../mfc/window-objects.md)