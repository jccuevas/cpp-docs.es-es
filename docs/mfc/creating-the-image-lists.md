---
title: Crear las listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 440ab6fdfe7663557f6c6a6607e617c793d26674
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371575"
---
# <a name="creating-the-image-lists"></a>Crear las listas de imágenes

Crear listas de imágenes es lo mismo tanto si se utiliza [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
> Solo necesita listas de imágenes `LVS_ICON` si el control de lista incluye el estilo.

Utilice `CImageList` la clase para crear una o más listas de imágenes (para iconos de tamaño completo, iconos pequeños y estados). Consulte [CImageList](../mfc/reference/cimagelist-class.md)y listar listas de [imágenes](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Llame a [CListCtrl::SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) para cada lista de imágenes; pasar un puntero `CImageList` al objeto adecuado.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
