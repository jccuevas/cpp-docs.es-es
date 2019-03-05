---
title: CTreeCtrl vs. CTreeView
ms.date: 11/04/2016
f1_keywords:
- CTreeCtrl
- CTreeView
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 29349e169e5ad8475001235d9b355da52156d683
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271637"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl vs. CTreeView

MFC proporciona dos clases que encapsulan los controles de árbol: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md). Cada clase es útil en situaciones diferentes.

Use `CTreeCtrl` cuando necesite un control de ventana secundaria plana; por ejemplo, en un cuadro de diálogo. Especialmente querría usar `CTreeCtrl` si habrá otros controles secundarios en la ventana, como se muestra en un cuadro de diálogo típico.

Use `CTreeView` si desea que el control de árbol para que actúe como una ventana de vista en la arquitectura documento/vista, así como un control de árbol. Un `CTreeView` ocupará toda el área cliente de una ventana de marco o ventana divisora. Se cambiará de tamaño automáticamente cuando se cambia el tamaño de su ventana primaria, y puede procesar mensajes de comandos de menús, teclas de aceleración y barras de herramientas. Puesto que un control de árbol contiene los datos necesarios para mostrar el árbol, el objeto de documento correspondiente no tiene que ser complicado, incluso podría usar [CDocument](../mfc/reference/cdocument-class.md) como el tipo de documento en la plantilla de documento.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
