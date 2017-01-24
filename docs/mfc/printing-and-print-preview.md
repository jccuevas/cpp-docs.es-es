---
title: "Impresi&#243;n y vista previa de impresi&#243;n | Microsoft Docs"
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
  - "vista previa de impresión"
  - "vista previa de impresión"
  - "imprimir [C++]"
  - "imprimir [C++], vista previa de impresión"
  - "imprimir [MFC]"
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Impresi&#243;n y vista previa de impresi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC admite la impresión y vista previa de impresión de documentos del programa mediante la clase [CView](../mfc/reference/cview-class.md).  Para la impresión básica y la vista previa de impresión, reemplace simplemente la función miembro de [OnDraw](../Topic/CView::OnDraw.md) de la clase de vista, que debe hacer de todos modos.  Esa función puede dibujar a la vista en la pantalla, un contexto de dispositivo de impresora para una impresora real, o un contexto de dispositivo que simule la impresora en la pantalla.  
  
 También puede agregar código para administrar la impresión y vista previa del documento de varias páginas, para paginar documentos impresos, y para agregar encabezados y pies de página a ellos.  
  
 Esta familia de casos explica cómo como se implementa en la biblioteca Microsoft Foundation Class \(MFC\) y cómo aprovechar la arquitectura de impresión compilada ya en el marco.  Los casos también explican cómo MFC admite la implementación fácil de la funcionalidad de vista previa de impresión y cómo utilizar y modificar esa funcionalidad.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Impresión](../mfc/printing.md)  
  
-   [Arquitectura de la vista previa de impresión](../mfc/print-preview-architecture.md)  
  
-   [Ejemplo](../top/visual-cpp-samples.md)  
  
## Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)