---
title: CTreeCtrl frente a CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 83e07c75b9eab6df05dbcd0f52cfbe8b90e1d768
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620481"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl frente a CTreeView

MFC proporciona dos clases que encapsulan controles de árbol: [CTreeCtrl](reference/ctreectrl-class.md) y [CTreeView](reference/ctreeview-class.md). Cada clase es útil en situaciones diferentes.

Use `CTreeCtrl` cuando necesite un control de ventana secundaria sin formato; por ejemplo, en un cuadro de diálogo. También podría querer usar `CTreeCtrl` si hay otros controles secundarios en la ventana, como en un cuadro de diálogo típico.

Use `CTreeView` cuando desee que el control de árbol actúe como una ventana de vista en la arquitectura de documento/vista, así como un control de árbol. Un `CTreeView` ocupará todo el área de cliente de una ventana de marco o una ventana divisora. Se cambiará automáticamente de tamaño cuando se cambie el tamaño de la ventana primaria y podrá procesar los mensajes de comandos de los menús, las teclas de aceleración y las barras de herramientas. Dado que un control de árbol contiene los datos necesarios para mostrar el árbol, el objeto de documento correspondiente no tiene que ser complicado. incluso podría usar [CDocument](reference/cdocument-class.md) como el tipo de documento en la plantilla de documento.

## <a name="see-also"></a>Consulte también

[Usar CTreeCtrl](using-ctreectrl.md)<br/>
[Permite](controls-mfc.md)
