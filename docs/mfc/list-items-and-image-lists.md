---
title: Elementos de lista y listas de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
ms.openlocfilehash: 77dd2f6a056ca74ff3334878a9cf1ef51c773335
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508358"
---
# <a name="list-items-and-image-lists"></a>Elementos de lista y listas de imágenes

Un "elemento" en un control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) se compone de un icono, una etiqueta y, posiblemente, otra información (en "subelementos").

Los iconos de los elementos de control de lista se incluyen en las listas de imágenes. Una lista de imágenes contiene iconos de tamaño completo usados en la vista de iconos. Una segunda lista de imágenes, opcional, contiene versiones más pequeñas de los mismos iconos para su uso en otras vistas del control. Una tercera lista opcional contiene imágenes de "estado", como casillas, para mostrar delante de los iconos pequeños en algunas vistas. Una cuarta lista opcional contiene las imágenes que se muestran en los elementos de encabezado individuales del control de lista.

> [!NOTE]
>  Si se crea un control de vista de lista con el estilo LVS_SHAREIMAGELISTS, es responsabilidad suya destruir las listas de imágenes cuando ya no estén en uso. Especifique este estilo si asigna las mismas listas de imágenes a varios controles de vista de lista; de lo contrario, es posible que más de un control intente destruir la misma lista de imágenes.

Para obtener más información acerca de los elementos de lista, vea [List View Image](/windows/win32/Controls/using-list-view-controls) lists and [Items and](/windows/win32/Controls/using-list-view-controls) SubItems in the Windows SDK. Vea también la clase [CImageList](../mfc/reference/cimagelist-class.md) en la *referencia de MFC* y el uso de [CImageList](../mfc/using-cimagelist.md) en esta familia de artículos.

Para crear un control de lista, debe proporcionar listas de imágenes que se usarán al insertar nuevos elementos en la lista. En el ejemplo siguiente se muestra este procedimiento, donde *m_pImagelist* es un puntero `CImageList` de tipo y m_listctrl `CListCtrl` es un miembro de datos.

[!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]

Sin embargo, si no tiene previsto Mostrar iconos en la vista de lista o en el control de lista, no necesita listas de imágenes.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
