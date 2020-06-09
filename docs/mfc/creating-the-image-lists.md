---
title: Crear las listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
ms.openlocfilehash: bbba01a6a8e08ea53e164656733aa06e03dd87a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625944"
---
# <a name="creating-the-image-lists"></a>Crear las listas de imágenes

La creación de listas de imágenes es la misma si utiliza [CListView](reference/clistview-class.md) o [CListCtrl](reference/clistctrl-class.md).

> [!NOTE]
> Solo necesita listas de imágenes si el control de lista incluye el `LVS_ICON` estilo.

Use la clase `CImageList` para crear una o varias listas de imágenes (para iconos de tamaño completo, iconos pequeños y Estados). Vea [CImageList](reference/cimagelist-class.md)y ver [listas de imágenes de vista de lista](/windows/win32/Controls/using-list-view-controls) en el Windows SDK.

Llame a [CListCtrl:: SetImageList](reference/clistctrl-class.md#setimagelist) para cada lista de imágenes; Pase un puntero al objeto adecuado `CImageList` .

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](using-clistctrl.md)<br/>
[Permite](controls-mfc.md)
