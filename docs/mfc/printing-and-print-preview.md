---
title: Impresión y vista previa de impresión | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8a26bac196dbddc6c05df5850225d05f432bc566
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="printing-and-print-preview"></a>Impresión y vista previa de impresión
MFC es compatible con la vista previa de impresión y documentos del programa mediante una clase [CView](../mfc/reference/cview-class.md). Para la impresión básica y vista previa de impresión, simplemente reemplace la clase de vista [OnDraw](../mfc/reference/cview-class.md#ondraw) función miembro, lo que debe hacer de todos modos. Esa función puede dibujar en la vista en la pantalla, en un contexto de dispositivo de impresora para una impresora real, o a un contexto de dispositivo simula la impresora en la pantalla.  
  
 También puede agregar código para administrar la impresión de documentos de varias páginas y vista previa, que se va a paginar los documentos impresos como agregar encabezados y pies de página a ellos.  
  
 Esta serie de artículos explica cómo implementar la impresión en la biblioteca de clases de Microsoft Foundation (MFC) y cómo aprovechar las ventajas de la arquitectura de impresión ya integrada en el marco de trabajo. Los artículos también explican cómo MFC es compatible con una implementación sencilla de la funcionalidad de vista previa de impresión y cómo puede utilizar y modificar esa funcionalidad.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Impresión](../mfc/printing.md)  
  
-   [Arquitectura de vista previa de impresión](../mfc/print-preview-architecture.md)  
  
-   [Ejemplo](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
