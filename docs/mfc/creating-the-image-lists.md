---
title: "Crear las listas de imágenes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], creating image lists for
- image lists [MFC], creating for CListCtrl
- lists [MFC], image
ms.assetid: c2768515-deba-49e8-a6f3-5be6482afb19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bfb42dc2c14b5092aeb667ea22008abe4d581a6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-image-lists"></a>Crear las listas de imágenes
Crear listas de imágenes es el mismo independientemente de si usa [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md).  
  
> [!NOTE]
>  Crear solo necesita la imagen listas si el control de lista incluye el `LVS_ICON` estilo.  
  
 Utilice la clase `CImageList` para crear una o varias listas de imágenes (para iconos de tamaño normal, iconos pequeños y estados). Vea [CImageList](../mfc/reference/cimagelist-class.md)y vea [listas de imágenes de vista de lista](http://msdn.microsoft.com/library/windows/desktop/bb774736) del SDK de Windows.  
  
 Llame a [CListCtrl:: SetImageList](../mfc/reference/clistctrl-class.md#setimagelist) para cada imagen de la lista; pasar un puntero a la correspondiente `CImageList` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

