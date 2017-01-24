---
title: "Rol de la vista en la impresi&#243;n | Microsoft Docs"
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
  - "CView (clase), rol en impresión"
  - "OnDraw (método), e impresión"
  - "imprimir [MFC], OnDraw (método)"
  - "imprimir [MFC], vistas"
  - "imprimir vistas"
  - "vistas, imprimir"
ms.assetid: 8d4a3c8e-1fce-4edc-b608-94cb5f3e487e
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Rol de la vista en la impresi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La vista también desempeña dos roles principales de imprimir el documento asociado.  
  
 La vista:  
  
-   Utiliza el mismo código de [OnDraw](../Topic/CView::OnDraw.md) para dibujar en la impresora acerca de dibujo en la pantalla.  
  
-   Administra dividir el documento en las páginas para imprimir.  
  
 Para obtener más información sobre cómo imprimir y el rol de la vista en la impresión, vea [Impresión y vista previa de impresión](../mfc/printing-and-print-preview.md).  
  
## Vea también  
 [Usar vistas](../mfc/using-views.md)