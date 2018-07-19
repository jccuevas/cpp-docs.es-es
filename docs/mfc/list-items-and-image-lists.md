---
title: Elementos de lista y listas de imágenes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], and list items
- image lists [MFC], list items
- CListCtrl class [MFC], image lists
- list items [MFC], image lists
ms.assetid: 317d095f-f978-47da-acb6-7bfe7dd3bc69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e12c212939a708a4411a28bff0ebe5026a21b1e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932135"
---
# <a name="list-items-and-image-lists"></a>Elementos de lista y listas de imágenes
Un "elemento" en un control de lista ([CListCtrl](../mfc/reference/clistctrl-class.md)) consta de un icono, una etiqueta y, posiblemente, otra información (en "subelementos").  
  
 Los iconos de elementos de control de lista se encuentran en listas de imágenes. Una lista de imágenes contiene iconos de tamaño completo que se usan en la vista de iconos. Una lista de imágenes en segundo lugar, opcional, contiene versiones reducidas de los mismos iconos para su uso en otras vistas del control. Una tercera lista opcional contiene imágenes de "estado", por ejemplo, casillas, para mostrar delante de los iconos pequeños en determinadas vistas. Una cuarta lista opcional contiene imágenes que se muestran en elementos de encabezado individuales del control de lista.  
  
> [!NOTE]
>  Si se crea un control de vista de lista con el estilo LVS_SHAREIMAGELISTS, es responsable de destruirlo las listas de imágenes cuando ya no están en uso. Especifique este estilo si asigna la misma imagen listas a varios controles de vista de lista; en caso contrario, más de un control podría intentar destruir la misma lista de imágenes.  
  
 Para obtener más información acerca de los elementos de lista, vea [listas de imágenes de vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774736) y [elementos y subelementos](http://msdn.microsoft.com/library/windows/desktop/bb774736) del SDK de Windows. Vea también la clase [CImageList](../mfc/reference/cimagelist-class.md) en el *referencia de MFC* y [utilizar CImageList](../mfc/using-cimagelist.md) de esta familia de artículos.  
  
 Para crear un control de lista, debe proporcionar listas de imágenes que se usarán al insertar nuevos elementos en la lista. En el ejemplo siguiente se muestra este procedimiento, donde *m_pImagelist* es un puntero de tipo `CImageList` y *m_listctrl* es un `CListCtrl` miembro de datos.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#19](../mfc/codesnippet/cpp/list-items-and-image-lists_1.cpp)]  
  
 Sin embargo, si no tiene pensado mostrar iconos en la vista de lista o el control de lista, no tiene listas de imágenes.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

