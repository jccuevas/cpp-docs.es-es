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
ms.openlocfilehash: f15256f99a744273b3487925bf273ad563c32aff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450809"
---
# <a name="rubber-banding-and-trackers"></a>Efecto de banda elástica y seguimiento

Otra característica proporcionada con los objetos de seguimiento es la selección de "banda de goma", lo que permite al usuario seleccionar varios elementos OLE arrastrando un rectángulo de tamaño alrededor de los elementos que se seleccionen. Cuando el usuario suelta el botón primario del mouse, se seleccionan elementos dentro de la región seleccionada por el usuario y se pueden manipular por el usuario. Por ejemplo, el usuario podría arrastrar la selección en otra aplicación de contenedor.

La implementación de esta característica requiere código adicional en función de controlador WM_LBUTTONDOWN de la aplicación.

Ejemplo de código siguiente implementa características adicionales y selección de banda de goma.

[!code-cpp[NVC_MFCOClient#6](../mfc/codesnippet/cpp/rubber-banding-and-trackers_1.cpp)]

Si desea permitir una orientación reversible del rastreador durante las bandas de goma, debe llamar a [CRectTracker:: TrackRubberBand](../mfc/reference/crecttracker-class.md#trackrubberband) con el tercer parámetro establecido en **TRUE**. Recuerde que a veces hará que lo que permite una orientación reversible [CRectTracker::m_rect](../mfc/reference/crecttracker-class.md#m_rect) a convertirse en invertido. Esto puede corregirse mediante una llamada a [CRect:: NormalizeRect](../atl-mfc-shared/reference/crect-class.md#normalizerect).

Para obtener más información, consulte [los elementos de cliente de contenedor](../mfc/containers-client-items.md) y [personalización de arrastrar y colocar](../mfc/drag-and-drop-customizing.md).

## <a name="see-also"></a>Vea también

[Seguimiento: Implementar el seguimiento en la aplicación OLE](../mfc/trackers-implementing-trackers-in-your-ole-application.md)<br/>
[CRectTracker (clase)](../mfc/reference/crecttracker-class.md)
