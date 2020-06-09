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
ms.openlocfilehash: 26ced8172a36d34883d6b65997bb3a81fdc3c319
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625279"
---
# <a name="printing-and-print-preview"></a>Impresión y vista previa de impresión

MFC admite la impresión y la vista previa de impresión para los documentos del programa a través de la clase [CView](reference/cview-class.md). Para la impresión básica y la vista previa de impresión, simplemente invalide la función miembro [OnDraw](reference/cview-class.md#ondraw) de la clase de vista, que debe hacer de todos modos. Esa función puede dibujar en la vista de la pantalla, en un contexto de dispositivo de impresora para una impresora real o en un contexto de dispositivo que simula la impresora en la pantalla.

También puede agregar código para administrar la impresión y la vista previa de documentos de páginas multipágina, para paginar los documentos impresos y para agregarles encabezados y pies de página.

Esta familia de artículos explica cómo se implementa la impresión en el biblioteca MFC (MFC) y cómo sacar partido de la arquitectura de impresión ya integrada en el marco de trabajo. En los artículos también se explica cómo MFC admite la implementación sencilla de la funcionalidad de vista previa de impresión y cómo se puede usar y modificar esa funcionalidad.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Impresión](printing.md)

- [Arquitectura de vista previa de impresión](print-preview-architecture.md)

- [Ejemplo](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Consulte también

[Elementos de la interfaz de usuario](user-interface-elements-mfc.md)
