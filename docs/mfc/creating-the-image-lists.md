---
title: Crear las listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: 6687b62b70103894d957a21019008e8781385feb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508783"
---
# <a name="creating-the-image-lists"></a>Crear las listas de imágenes

La creación de listas de imágenes es la misma si utiliza [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md).

> [!NOTE]
>  Solo necesita listas de imágenes si el control de lista incluye `LVS_ICON` el estilo.

Use la `CImageList` clase para crear una o varias listas de imágenes (para iconos de tamaño completo, iconos pequeños y Estados). Vea [CImageList](../mfc/reference/cimagelist-class.md)y ver [listas de imágenes de vista de lista](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Llame a [CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) para cada lista de imágenes; Pase un puntero al objeto adecuado `CImageList` .

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
