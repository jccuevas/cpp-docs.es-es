---
title: Efecto de banda elástica y seguimiento
ms.date: 11/04/2016
helpviewer_keywords:
- trackers [MFC]
- CRectTracker class [MFC], implementing trackers
- OLE objects [MFC], selecting
- rubber banding [MFC]
- WM_LBUTTONDOWN [MFC]
ms.assetid: 0d0fa64c-6418-4baf-ab7f-2d16ca039230
ms.openlocfilehash: 095f3c15546466c6a495f6aa348990ed69b04a9e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127371"
---
# <a name="rubber-banding-and-trackers"></a>Efecto de banda elástica y seguimiento

Otra característica suministrada con los rastreadores es la selección de "banda elástica", que permite al usuario seleccionar varios elementos OLE arrastrando un rectángulo de ajuste de tamaño alrededor de los elementos que se van a seleccionar. Cuando el usuario suelta el botón primario del mouse, se seleccionan los elementos dentro de la región seleccionada por el usuario y el usuario puede manipularlos. Por ejemplo, el usuario puede arrastrar la selección a otra aplicación contenedora.

La implementación de esta característica requiere código adicional en la función de controlador de WM_LBUTTONDOWN de la aplicación.

En el ejemplo de código siguiente se implementa la selección de banda elástica y características adicionales.

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

Si desea permitir la orientación reversible del rastreador durante la banda elástica, debe llamar a [CRectTracker:: TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) con el tercer parámetro establecido en **true**. Recuerde que, al permitir la orientación reversible, a veces se provocará que [CRectTracker:: m_rect](../mfc/reference/crecttracker-class.md#m_rect) se invierta. Esto puede corregirse mediante una llamada a [CRect:: NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).

Para obtener más información, vea [elementos de cliente de contenedor](../mfc/containers-client-items.md) y [arrastrar y colocar de OLE: personalizar la función de arrastrar y colocar](../mfc/drag-and-drop-ole.md#customize-drag-and-drop).

## <a name="see-also"></a>Consulte también

[Seguimiento: Implementar el seguimiento en la aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker (clase)](../mfc/reference/crecttracker-class.md)
