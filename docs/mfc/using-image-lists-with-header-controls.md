---
title: Usar listas de imágenes con controles de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
ms.openlocfilehash: 8002c16d1cdf5e0683b642001409b6da9c260660
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366471"
---
# <a name="using-image-lists-with-header-controls"></a>Usar listas de imágenes con controles de encabezado

Los elementos de encabezado tienen la capacidad de mostrar una imagen dentro de un elemento de encabezado. Esta imagen, almacenada en una lista de imágenes asociada, es de 16 x 16 píxeles y tiene las mismas características que las imágenes de icono utilizadas en un control de vista de lista. Para implementar este comportamiento correctamente, primero debe crear e inicializar la lista de imágenes, asociar la lista con el control de encabezado y, a continuación, modificar los atributos del elemento de encabezado que mostrará la imagen.

El siguiente procedimiento ilustra los detalles, utilizando`m_pHdrCtrl`un puntero a un`m_pHdrImages`control de encabezado ( ) y un puntero a una lista de imágenes ( ).

### <a name="to-display-an-image-in-a-header-item"></a>Para mostrar una imagen en un elemento de encabezado

1. Construir una nueva lista de imágenes (o usar un objeto de lista de imágenes existente) mediante el [CImageList](../mfc/reference/cimagelist-class.md) constructor, almacenar el puntero resultante.

1. Inicializar el nuevo objeto de lista de imágenes llamando a [CImageList::Create](../mfc/reference/cimagelist-class.md#create). El código siguiente es un ejemplo de esta llamada.

   [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]

1. Agregue las imágenes para cada elemento de encabezado. El código siguiente agrega dos imágenes predefinidas.

   [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]

1. Asocie la lista de imágenes con el control de encabezado con una llamada a [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).

1. Modifique el elemento de encabezado para mostrar una imagen de la lista de imágenes asociada. En el ejemplo siguiente se `m_phdrImages`asigna la primera imagen, de , al primer elemento de encabezado, `m_pHdrCtrl`.

   [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]

Para obtener información detallada sobre los valores de parámetro utilizados, consulte el [cHeaderCtrl](../mfc/reference/cheaderctrl-class.md)pertinente.

> [!NOTE]
> Es posible tener varios controles utilizando la misma lista de imágenes. Por ejemplo, en un control de vista de lista estándar, podría haber una lista de imágenes (de imágenes de 16 x 16 píxeles) utilizada por la vista de icono pequeño de un control de vista de lista y los elementos de encabezado del control de vista de lista.

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)
