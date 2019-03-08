---
title: Dibujar imágenes a partir de una lista de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: e2058c727620c9aae4ccd9a3fbeaae02c78ce8c6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57260535"
---
# <a name="drawing-images-from-an-image-list"></a>Dibujar imágenes a partir de una lista de imágenes

Para dibujar una imagen, use el [CImageList::Draw](../mfc/reference/cimagelist-class.md#draw) función miembro. Especifique un puntero a un objeto de contexto de dispositivo, el índice de la imagen para dibujar, la ubicación en el contexto de dispositivo en el que se va a dibujar la imagen y un conjunto de marcas que indican el estilo de dibujo.

Al especificar el **ILD_TRANSPARENT** estilo, `Draw` usa un proceso de dos pasos para dibujar una imagen enmascarada. En primer lugar, realiza una operación lógica- y operación en los bits de la imagen y los bits de la máscara. A continuación, realiza una operación XOR lógica en los resultados de la primera operación y los bits de fondo del contexto del dispositivo de destino. Este proceso crea áreas transparentes en la imagen resultante. es decir, cada bit en la máscara de blanco hace que el bit correspondiente en la imagen resultante para ser transparente.

Antes de dibujar una imagen enmascarada en un fondo de color sólido, debe usar el [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) función miembro para establecer el color de fondo de la lista de imágenes en el mismo color que el destino. Establecer el color elimina la necesidad de crear áreas transparentes en la imagen y permite `Draw` simplemente copiar la imagen en el contexto de dispositivo de destino, lo que produce un aumento significativo del rendimiento. Para dibujar la imagen, especifique el **ILD_NORMAL** aplicar estilo al llamar a `Draw`.

Puede establecer el color de fondo para obtener una lista de imágenes enmascarada ([CImageList](../mfc/reference/cimagelist-class.md)) en cualquier momento, por lo que se dibuja correctamente en cualquier fondo sólido. Establecer el color de fondo en **como CLR_NONE** hace que las imágenes dibujar de forma transparente de forma predeterminada. Para recuperar el color de fondo de una lista de imágenes, use la [función miembro GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) función miembro.

El **ILD_BLEND25** y **ILD_BLEND50** estilos de interpolación de la imagen con el color de resaltado del sistema. Estos estilos son útiles si usa una imagen enmascarada para representar un objeto que el usuario puede seleccionar. Por ejemplo, puede usar el **ILD_BLEND50** estilo para dibujar la imagen cuando el usuario lo selecciona.

Una imagen no enmascarada se copia en el contexto de dispositivo de destino mediante el `SRCCOPY` operación de trama. Los colores de la imagen tienen el mismo independientemente del color de fondo del contexto del dispositivo. Los estilos de dibujo especificados en `Draw` tampoco tienen ningún efecto en la apariencia de una imagen no enmascarada.

Además de la función miembro Draw, otra función [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), amplía la capacidad de representar una imagen. `DrawIndirect` toma como parámetro, un [estructura IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) estructura. Esta estructura puede utilizarse para personalizar la representación de la imagen actual, incluido el uso de códigos de operación (superior) con trama. Para obtener más información sobre los códigos superior, consulte [códigos de operación de trama](/windows/desktop/gdi/raster-operation-codes) y [mapas de bits como pinceles](/windows/desktop/gdi/bitmaps-as-brushes) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)
