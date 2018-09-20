---
title: Impresión y vista previa de impresión | Microsoft Docs
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
ms.openlocfilehash: 9aad5c69f6466ea8803cb466c5e5529f3dce1340
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374458"
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
