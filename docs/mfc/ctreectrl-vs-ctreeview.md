---
title: CTreeCtrl frente a CTreeView
ms.date: 11/04/2016
helpviewer_keywords:
- tree view controls
- CTreeCtrl class [MFC], vs. CTreeView class [MFC]
- CTreeView class [MFC], vs. CTreeCtrl class [MFC]
- tree controls [MFC], and tree view
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
ms.openlocfilehash: 7c78dfa9920c913fdbedb009c5a6f275a3e3e273
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445230"
---
# <a name="ctreectrl-vs-ctreeview"></a>CTreeCtrl frente a CTreeView

MFC proporciona dos clases que encapsulan controles de árbol: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) y [CTreeView](../mfc/reference/ctreeview-class.md). Cada clase es útil en situaciones diferentes.

Utilice `CTreeCtrl` cuando necesite un control de ventana secundaria sin formato; por ejemplo, en un cuadro de diálogo. Lo más conveniente es usar `CTreeCtrl` si hay otros controles secundarios en la ventana, como en un cuadro de diálogo típico.

Utilice `CTreeView` cuando desee que el control de árbol actúe como una ventana de vista en la arquitectura de documento/vista, así como un control de árbol. Un `CTreeView` ocupará todo el área de cliente de una ventana de marco o una ventana divisora. Se cambiará automáticamente de tamaño cuando se cambie el tamaño de la ventana primaria y podrá procesar los mensajes de comandos de los menús, las teclas de aceleración y las barras de herramientas. Dado que un control de árbol contiene los datos necesarios para mostrar el árbol, el objeto de documento correspondiente no tiene que ser complicado. incluso podría usar [CDocument](../mfc/reference/cdocument-class.md) como el tipo de documento en la plantilla de documento.

## <a name="see-also"></a>Consulte también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
