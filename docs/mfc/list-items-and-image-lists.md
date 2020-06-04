---
title: Elementos de lista y listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: d378c6e07280349f9995981ad794039ebc015b25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353050"
---
# <a name="list-items-and-image-lists"></a>Elementos de lista y listas de imágenes

Un "elemento" en un control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) consta de un icono, una etiqueta y posiblemente otra información (en "subelementos").

Los iconos de los elementos de control de lista están contenidos en listas de imágenes. Una lista de imágenes contiene iconos de tamaño completo utilizados en la vista de iconos. Una segunda lista de imágenes opcional contiene versiones más pequeñas de los mismos iconos para su uso en otras vistas del control. Una tercera lista opcional contiene imágenes de "estado", como casillas de verificación, para mostrarlas delante de los iconos pequeños en determinadas vistas. Una cuarta lista opcional contiene imágenes que se muestran en elementos de encabezado individuales del control de lista.

> [!NOTE]
> Si se crea un control de vista de lista con el estilo LVS_SHAREIMAGELISTS, es responsable de destruir las listas de imágenes cuando ya no estén en uso. Especifique este estilo si asigna las mismas listas de imágenes a varios controles de vista de lista; de lo contrario, más de un control podría intentar destruir la misma lista de imágenes.

Para obtener más información acerca de los elementos de lista, vea [Listar listas](/windows/win32/Controls/using-list-view-controls) de imágenes y [elementos y subelementos](/windows/win32/Controls/using-list-view-controls) en el Windows SDK. Vea también la clase [CImageList](../mfc/reference/cimagelist-class.md) en la *referencia de MFC* y el uso de [CImageList](../mfc/using-cimagelist.md) en esta familia de artículos.

Para crear un control de lista, debe proporcionar listas de imágenes que se utilizarán al insertar nuevos elementos en la lista. En el ejemplo siguiente se muestra este procedimiento, donde `CListCtrl` *m_pImagelist* es un puntero de tipo `CImageList` y *m_listctrl* es un miembro de datos.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Sin embargo, si no tiene previsto mostrar iconos en la vista de lista o el control de lista, no necesita listas de imágenes.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
