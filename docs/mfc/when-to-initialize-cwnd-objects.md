---
title: "Cu&#225;ndo inicializar los objetos CWnd | Microsoft Docs"
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
  - "objetos CWnd, cuándo HWND está asociado"
  - "objetos CWnd, cuándo se debe inicializar"
  - "HWND, cuándo se asocia al objeto CWnd"
  - "inicializar objetos CWnd"
  - "inicializar objetos, CWnd"
  - "Window (objetos), cuándo se debe inicializar CWnd"
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cu&#225;ndo inicializar los objetos CWnd
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No puede crear dispone de las ventanas secundarias o llamar a una API de Windows funciona en el constructor de `CWnd`\- objeto derivado.  Esto es porque `HWND` para el objeto de `CWnd` no se ha creado.  La mayoría de inicialización Windows\- específica, como ventanas secundarias de suma, se debe hacer en un controlador de mensajes [OnCreate](../Topic/CWnd::OnCreate.md) .  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
-   [Creación de documentos y vistas](../mfc/document-view-creation.md)  
  
## Vea también  
 [Usar ventanas de marco](../mfc/using-frame-windows.md)