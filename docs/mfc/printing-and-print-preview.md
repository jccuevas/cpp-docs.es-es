---
title: Impresión y vista previa de impresión
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 4ca6663aefce219fad4d2e3be74215d2a78206a8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57263668"
---
# <a name="printing-and-print-preview"></a>Impresión y vista previa de impresión

MFC es compatible con vista previa de impresión y documentos de su programa a través de la clase [CView](../mfc/reference/cview-class.md). Para la impresión básica y vista previa de impresión, simplemente reemplace la clase de vista [OnDraw](../mfc/reference/cview-class.md#ondraw) función miembro, lo que debe hacer de todos modos. Puede dibujar esa función en la vista en la pantalla, en un contexto de dispositivo de impresora para una impresora real, o a un contexto de dispositivo simula la impresora en la pantalla.

También puede agregar código para administrar la impresión de varias páginas del documento y vista previa, para paginar los documentos impresos y para agregar encabezados y pies de página a ellos.

Esta serie de artículos explica cómo implementar la impresión en la biblioteca de clases de Microsoft Foundation (MFC) y cómo aprovechar las ventajas de la arquitectura de impresión ya integrada en el marco de trabajo. Los artículos también explican cómo MFC es compatible con una implementación sencilla de la funcionalidad de vista previa de impresión y cómo puede utilizar y modificar esa funcionalidad.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Impresión](../mfc/printing.md)

- [Arquitectura de vista previa de impresión](../mfc/print-preview-architecture.md)

- [Ejemplo](../visual-cpp-samples.md)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
