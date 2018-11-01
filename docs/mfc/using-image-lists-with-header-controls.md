---
title: Usar listas de imágenes con controles de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 5c623024ef64f49e3379ef02154cda72d445a197
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50545254"
---
# <a name="using-image-lists-with-header-controls"></a>Usar listas de imágenes con controles de encabezado

Los elementos de encabezado tienen la capacidad para mostrar una imagen dentro de un elemento de encabezado. Esta imagen, almacenada en una lista de imágenes asociada, es 16 x 16 píxeles y tiene las mismas características que las imágenes de icono utilizadas en un control de vista de lista. Para poder implementar correctamente este comportamiento, debe crear primero e inicializar la lista de imágenes, asociar el control de encabezado en la lista y, a continuación, modifique los atributos del elemento de encabezado que se mostrará la imagen.

El procedimiento siguiente muestra los detalles, mediante un puntero a un control de encabezado (`m_pHdrCtrl`) y un puntero a una lista de imágenes (`m_pHdrImages`).

### <a name="to-display-an-image-in-a-header-item"></a>Para mostrar una imagen en un elemento de encabezado

1. Construir una lista de imágenes (o utilice un objeto de lista de imágenes existente) mediante el [CImageList](../mfc/reference/cimagelist-class.md) constructor, almacenando el puntero resultante.

1. Inicializar el nuevo objeto de lista de imágenes mediante una llamada a [CImageList:: Create](../mfc/reference/cimagelist-class.md#create). El código siguiente es un ejemplo de esta llamada.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Agregar las imágenes para cada elemento de encabezado. El código siguiente agrega dos imágenes predefinidas.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Asociar la lista de imágenes con el control de encabezado con una llamada a [CHeaderCtrl:: SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Modifique el elemento de encabezado para mostrar una imagen de la lista de imágenes asociado. En el ejemplo siguiente se asigna la primera imagen, desde `m_phdrImages`, en el primer elemento de encabezado, `m_pHdrCtrl`.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Para obtener información detallada sobre los valores de parámetro utilizados, consulte la información pertinente [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).

> [!NOTE]
>  Es posible tener varios controles mediante la misma lista de imágenes. Por ejemplo, en un control de vista de lista estándar, podría haber una lista de imágenes (de imágenes de 16 x 16 píxeles) que se usan ambas la vista de iconos pequeños de un control de vista de lista y los elementos de encabezado del control de vista de lista.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

