---
title: Encabezados y pies de página | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c82df1a77cdbf677a6b5e6f84c371da243b9b08d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348255"
---
# <a name="headers-and-footers"></a>Encabezados y pies de página
En este artículo se explica cómo agregar encabezados y pies de página a un documento impreso.  
  
 Al examinar un documento en la pantalla, el nombre del documento y su ubicación actual en el documento se muestran normalmente en una barra de título y una barra de estado. Al examinar una copia impresa de un documento, resulta útil tener el nombre y número de página que se muestra en un encabezado o pie de página. Se trata de una forma común de en qué WYSIWYG incluso programas difieren en cómo realizar la impresión y visualización en pantalla.  
  
 El [OnPrint](../mfc/reference/cview-class.md#onprint) función miembro es el lugar adecuado para imprimir encabezados o pies de página porque se llama para cada página, y porque se llama solo para la impresión, no para la presentación en pantalla. Puede definir una función diferente para imprimir un encabezado o pie de página y pase el contexto de dispositivo de impresora desde `OnPrint`. Tendrá que ajustar el origen de la ventana o la extensión antes de llamar a [OnDraw](../mfc/reference/cview-class.md#ondraw) para evitar que el cuerpo de la superposición del encabezado o pie de página. Es posible que también deba modificar `OnDraw` porque podría reducirse la cantidad del documento que quepa en la página.  
  
 Una manera de compensar para el área ocupada por el encabezado o pie de página es utilizar el **m_rectDraw** miembro de [CPrintInfo](../mfc/reference/cprintinfo-structure.md). Cada vez que se imprime una página, este miembro se inicializa con el área utilizable de la página. Si imprime un encabezado o pie de página antes de imprimir el cuerpo de la página, puede reducir el tamaño del rectángulo que se almacenan en **m_rectDraw** para tener en cuenta el área ocupada por el encabezado o pie de página. A continuación, `OnPrint` pueden hacer referencia a **m_rectDraw** para averiguar cuánto área que queda para imprimir el cuerpo de la página.  
  
 No se puede imprimir un encabezado, o cualquier otra cosa, desde [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc), porque se llama antes de la `StartPage` función miembro de [CDC](../mfc/reference/cdc-class.md) se ha llamado. En ese momento, el contexto de dispositivo de impresora se considera en un límite de página. Puede realizar la impresión solo desde el `OnPrint` función miembro.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Imprimir documentos de varias páginas](../mfc/multipage-documents.md)  
  
-   [Asignar recursos de GDI para imprimir](../mfc/allocating-gdi-resources.md)  
  
## <a name="see-also"></a>Vea también  
 [Impresión](../mfc/printing.md)

