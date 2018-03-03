---
title: "Usar listas de imágenes con controles de encabezado | Documentos de Microsoft"
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
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7a51aadc10a7722875597813e24ceb5960ab459
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-image-lists-with-header-controls"></a>Usar listas de imágenes con controles de encabezado
Elementos de encabezado tienen la capacidad para mostrar una imagen dentro de un elemento de encabezado. Esta imagen, almacenada en una lista de imágenes asociada, es de 16 x 16 píxeles y tiene las mismas características que las imágenes de icono utilizadas en un control de vista de lista. Para implementar correctamente este comportamiento, debe crear en primer lugar e inicializar la lista de imágenes, asociar la lista con el control de encabezado y, a continuación, modifique los atributos del elemento de encabezado que se mostrará la imagen.  
  
 El procedimiento siguiente muestra los detalles, mediante un puntero a un control de encabezado (`m_pHdrCtrl`) y un puntero a una lista de imágenes (`m_pHdrImages`).  
  
### <a name="to-display-an-image-in-a-header-item"></a>Para mostrar una imagen en un elemento de encabezado  
  
1.  Crear una nueva lista de imágenes (o utilice un objeto de lista de imágenes existente) mediante la [CImageList](../mfc/reference/cimagelist-class.md) constructor, almacenando el puntero resultante.  
  
2.  Inicializar el nuevo objeto de lista de imagen mediante una llamada a [CImageList:: Create](../mfc/reference/cimagelist-class.md#create). El código siguiente es un ejemplo de esta llamada.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]  
  
3.  Agregar las imágenes para cada elemento de encabezado. El código siguiente agrega dos imágenes predefinidas.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]  
  
4.  Asociar la lista de imágenes con el control de encabezado con una llamada a [CHeaderCtrl:: SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).  
  
5.  Modifique el elemento de encabezado para mostrar una imagen desde la lista de imágenes asociada. En el ejemplo siguiente se asigna la primera imagen, desde `m_phdrImages`, para el primer elemento de encabezado, `m_pHdrCtrl`.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]  
  
 Para obtener información detallada sobre los valores de parámetro utilizados, consulte la pertinente [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).  
  
> [!NOTE]
>  Es posible tener varios controles que utilicen la misma lista de imágenes. Por ejemplo, en un control de vista de lista estándar, podría haber una lista de imágenes (de imágenes de 16 x 16 píxeles) utilizada por la vista de iconos pequeños de un control de vista de lista y los elementos de encabezado del control de vista de lista.  
  
## <a name="see-also"></a>Vea también  
 [Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

