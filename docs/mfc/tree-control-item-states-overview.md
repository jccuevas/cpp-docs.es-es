---
title: Información general sobre los estados de los elementos de control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: bbeabf69f174fcf172808ff71f07ed05f1dc9675
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511042"
---
# <a name="tree-control-item-states-overview"></a>Información general sobre los estados de los elementos de control de árbol

Cada elemento de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) tiene un estado actual. Por ejemplo, un elemento se puede seleccionar, deshabilitar, expandir, etc. En su mayor parte, el control de árbol establece automáticamente el estado de un elemento para reflejar las acciones del usuario, como la selección de un elemento. Sin embargo, también puede establecer el estado de un elemento mediante la función miembro [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) y recuperar el estado actual de un elemento mediante la función miembro [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) . Para obtener una lista completa de los Estados de los elementos, consulte el artículo sobre las [constantes de control de vista de árbol](/windows/win32/Controls/tree-view-control-item-states) en el Windows SDK.

El estado actual de un elemento se especifica mediante el parámetro *nState* . Un control de árbol puede cambiar el estado de un elemento para reflejar una acción del usuario, como seleccionar el elemento o establecer el foco en el elemento. Además, una aplicación podría cambiar el estado de un elemento para deshabilitar u ocultar el elemento o para especificar una imagen de superposición o imagen de estado.

Al especificar o cambiar el estado de un elemento, el parámetro *nStateMask* especifica los bits de estado que se van a establecer y el parámetro *nState* contiene los nuevos valores de esos bits. Por ejemplo, en el ejemplo siguiente se cambia el estado actual de un elemento primario (especificado por *hParentItem*) `CTreeCtrl` en un`m_treeCtrl`objeto ( `TVIS_EXPANDPARTIAL`) a:

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

Otro ejemplo de cómo cambiar el estado sería establecer la imagen de superposición de un elemento. Para ello, *nStateMask* debe incluir el `TVIS_OVERLAYMASK` valor y *nState* debe incluir el índice basado en uno de la imagen de superposición desplazada a la izquierda ocho bits mediante la macro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) . El índice puede ser 0 para no especificar ninguna imagen de superposición. La imagen de superposición se debe haber agregado a la lista de imágenes superpuestas del control de árbol mediante una llamada anterior a la función [CImageList:: SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) . La función especifica el índice basado en uno de la imagen que se va a agregar; Este es el índice utilizado con la macro INDEXTOOVERLAYMASK. Un control de árbol puede tener hasta cuatro imágenes superpuestas.

Para establecer la imagen de estado de un elemento, *nStateMask* debe `TVIS_STATEIMAGEMASK` incluir el valor y *nState* debe incluir el índice basado en uno de la imagen de estado desplazada a la izquierda 12 bits mediante la macro [INDEXTOSTATEIMAGEMASK](/windows/win32/api/commctrl/nf-commctrl-indextostateimagemask) . El índice puede ser 0 para no especificar ninguna imagen de estado. Para obtener más información sobre las imágenes de superposición y estado, vea [listas de imágenes de control de árbol](../mfc/tree-control-image-lists.md).

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
