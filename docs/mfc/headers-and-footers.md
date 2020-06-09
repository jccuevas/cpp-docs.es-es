---
title: Encabezados y pies de página
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
ms.openlocfilehash: 7024c57dbe41a579582d409d0536db0ca0bc46d6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620106"
---
# <a name="headers-and-footers"></a>Encabezados y pies de página

En este artículo se explica cómo agregar encabezados y pies de página a un documento impreso.

Al mirar un documento en la pantalla, el nombre del documento y su ubicación actual en el documento se muestran normalmente en una barra de título y en una barra de estado. Al mirar una copia impresa de un documento, es útil tener el nombre y el número de página mostrados en un encabezado o pie de página. Se trata de una manera común en la que incluso los programas WYSIWYG difieren en cómo realizan la impresión y la presentación en pantalla.

La función miembro [OnPrint](reference/cview-class.md#onprint) es el lugar adecuado para imprimir encabezados o pies de página porque se llama en cada página, y porque solo se llama para imprimir, no para la presentación en pantalla. Puede definir una función independiente para imprimir un encabezado o un pie de página y pasarle el contexto de dispositivo de impresora `OnPrint` . Es posible que tenga que ajustar el origen o la extensión de la ventana antes de llamar a [OnDraw](reference/cview-class.md#ondraw) para evitar que el cuerpo de la página se solape con el encabezado o el pie de página. Es posible que también tenga que modificarla, ya que se puede `OnDraw` reducir la cantidad del documento que cabe en la página.

Una manera de compensar el área tomada por el encabezado o el pie de página es usar el miembro **m_rectDraw** de [CPrintInfo](reference/cprintinfo-structure.md). Cada vez que se imprime una página, este miembro se inicializa con el área utilizable de la página. Si imprime un encabezado o un pie de página antes de imprimir el cuerpo de la página, puede reducir el tamaño del rectángulo almacenado en **m_rectDraw** para tener en cuenta el área tomada por el encabezado o el pie de página. A continuación, `OnPrint` puede hacer referencia a **m_rectDraw** para averiguar la cantidad de área que queda para imprimir el cuerpo de la página.

No se puede imprimir un encabezado, o cualquier otro elemento, desde [OnPrepareDC](reference/cview-class.md#onpreparedc), porque se llama a este método antes de que se haya `StartPage` llamado a la función miembro de [CDC](reference/cdc-class.md) . En ese momento, se considera que el contexto del dispositivo de impresora está en el límite de la página. Solo puede realizar la impresión desde la `OnPrint` función miembro.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Imprimir documentos de páginas multipágina](multipage-documents.md)

- [Asignar recursos GDI para imprimir](allocating-gdi-resources.md)

## <a name="see-also"></a>Consulte también

[Impresión](printing.md)
