---
title: Crear las listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 52f375c98b5f73e0f5721c951c94e4b24f0bc224
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50608685"
---
# <a name="creating-the-image-lists"></a>Crear las listas de imágenes

Creación de listas de imágenes es el mismo independientemente de si usa [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Solo necesita listas de imágenes si el control de lista incluye el `LVS_ICON` estilo.

Utilice la clase `CImageList` para crear una o varias listas de imágenes (para iconos de tamaño normal, iconos pequeños y estados). Consulte [CImageList](../mfc/reference/cimagelist-class.md)y consulte [listas de imágenes de vista de lista](/windows/desktop/Controls/using-list-view-controls) en el SDK de Windows.

Llame a [CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) para cada lista de imágenes; pasar un puntero a la correspondiente `CImageList` objeto.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

