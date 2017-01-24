---
title: "Destruir el cuadro de di&#225;logo | Microsoft Docs"
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
  - "destrucción, cuadro de diálogo"
  - "cuadros de diálogo, eliminar"
  - "cuadros de diálogo, destruir"
  - "cuadros de diálogo, quitar"
  - "cuadros de diálogo de MFC, destruir"
  - "cuadros de diálogo modales, destruir"
  - "cuadros de diálogo no modales, destruir"
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Destruir el cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los cuadros de diálogo modales se crean en el marco de pila y se destruyen normalmente cuando la función que los creó finaliza.  Se llama al destructor del objeto de diálogo cuando el objeto salga del ámbito.  
  
 Los cuadros de diálogo no modal se crean y que normalmente por una ventana principal de vista o del cuadro de la ventana de marco principal de la aplicación o una ventana de marco de documento.  El controlador de [OnClose](../Topic/CWnd::OnClose.md) predeterminado llama [DestroyWindow](../Topic/CWnd::DestroyWindow.md), que destruye la ventana del cuadro de diálogo.  Si el cuadro de diálogo se coloca únicamente, sin punteros a él u otra semántica especial de la propiedad, debe invalidar [PostNcDestroy](../Topic/CWnd::PostNcDestroy.md) para destruir el objeto de cuadro de diálogo de C\+\+.  También debe reemplazar [OnCancel](../Topic/CDialog::OnCancel.md) y llamar a `DestroyWindow` dentro de.  Si no, el propietario del cuadro de diálogo debe destruir el objeto C\+\+ cuando ya no es necesario.  
  
## Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)