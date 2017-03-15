---
title: "Encabezados y pies de p&#225;gina | Microsoft Docs"
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
  - "pies de página, imprimir"
  - "encabezados, imprimir"
  - "pies de página"
  - "pies de página, imprimir"
  - "encabezados de página"
  - "encabezados de página, imprimir"
  - "imprimir [MFC], encabezados y pies de página"
  - "imprimir [MFC], documentos de varias páginas"
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Encabezados y pies de p&#225;gina
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo agregar encabezados y pies de página a un documento impreso.  
  
 Al examinar un documento en la pantalla, el nombre del documento y la ubicación actual del documento se muestran generalmente en una barra de título y una barra de estado.  Cuando se consulta una copia impresa de un documento, es útil tener el nombre y el número de página mostrados en un encabezado o pie de página.  Ésta es una manera común de la que incluso los programas WYSIWYG difieren en cómo realizan la impresión y la presentación en pantalla.  
  
 La función miembro de [OnPrint](../Topic/CView::OnPrint.md) es el lugar adecuado para imprimir encabezados o pies de página porque se llama para cada página y, dado que sólo se llama para imprimir, no para la presentación en pantalla.  Puede definir una función independiente para imprimir un encabezado o pie de página, y pásele el contexto de dispositivo de impresora de `OnPrint`.  Es posible que necesite ajustar el origen de ventana o extensión antes de que llamó [OnDraw](../Topic/CView::OnDraw.md) para evitar que el cuerpo de la página se superponga con el encabezado o el pie de página.  También podría tener que modificar `OnDraw` porque la cantidad de documento que cabrá en páginas podría disminuir.  
  
 Una manera de compensar el área realizada por el encabezado o el pie de página es utilizar el miembro de **m\_rectDraw** de [CPrintInfo](../mfc/reference/cprintinfo-structure.md).  Cada vez que se imprime una página, este miembro se inicializa con el área útil de la página.  Si imprime un encabezado o pie de página antes de imprimir el cuerpo de la página, puede reducir el tamaño del rectángulo almacenado en **m\_rectDraw** para explicar el área realizada por el encabezado o el pie de página.  A continuación `OnPrint` puede hacer referencia a **m\_rectDraw** para averiguar cuánto queda por área para imprimir el cuerpo de la página.  
  
 No puede imprimir un encabezado, o cualquier otra acción, de [OnPrepareDC](../Topic/CView::OnPrepareDC.md), porque se invoca antes de que la función miembro de `StartPage` de [CDC](../mfc/reference/cdc-class.md) se haya llamado a.  En ese momento, el contexto de dispositivo de impresora se considera estar en un límite de página.  Puede realizar imprimir en la función miembro de `OnPrint` .  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Documentos de varias páginas de impresión](../mfc/multipage-documents.md)  
  
-   [Asignar recursos de GDI para imprimir](../mfc/allocating-gdi-resources.md)  
  
## Vea también  
 [Imprimir](../mfc/printing.md)