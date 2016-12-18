---
title: "Destruir ventanas de marco | Microsoft Docs"
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
  - "PostNcDestroy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Default (método)"
  - "destruir ventanas de marco"
  - "DestroyWindow (método)"
  - "ventanas de marco de documento, destruir"
  - "ventanas de marco [C++], destruir"
  - "MFC [C++], ventanas de marco"
  - "OnClose (método)"
  - "OnNcDestroy (método), y ventanas de marco"
  - "PostNcDestroy (método)"
  - "ventanas [C++], destruir"
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Destruir ventanas de marco
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El marco de trabajo de MFC administra la destrucción de la ventana junto con la creación de esas ventanas asociadas al marco documentos ni vistas.  Si crea ventanas adicionales, es responsable de destruirlas.  
  
 En el marco, cuando el usuario cierra la ventana de marco, el controlador predeterminado de [OnClose](../Topic/CWnd::OnClose.md) de la ventana llama [DestroyWindow](../Topic/CWnd::DestroyWindow.md).  La función del último miembro denominada cuando se destruye la ventana de Windows es [OnNcDestroy](../Topic/CWnd::OnNcDestroy.md), que hace algún limpieza, llama a la función miembro de [valor predeterminado](../Topic/CWnd::Default.md) para realizar la limpieza de Windows, y llama a la función virtual [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md)miembro.  La implementación de [CFrameWnd](../mfc/reference/cframewnd-class.md) de `PostNcDestroy` elimina el objeto de la ventana de C\+\+.  Nunca debe utilizar el operador de C\+\+ **borrar** en una ventana de marco.  Utilice `DestroyWindow` en su lugar.  
  
 Cuando se cierra la ventana principal, la aplicación se cierra.  Si hay documentos no guardados modificados, el marco muestra un cuadro de mensaje para preguntar si se guardan los documentos y garantiza que los documentos adecuados se guardan en caso necesario.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
## Vea también  
 [Usar ventanas de marco](../mfc/using-frame-windows.md)