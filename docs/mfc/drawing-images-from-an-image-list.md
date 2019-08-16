---
title: Dibujar imágenes a partir de una lista de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: fb307d5557c0e136c1c44c29f08af6062bb1c19d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508610"
---
# <a name="drawing-images-from-an-image-list"></a>Dibujar imágenes a partir de una lista de imágenes

Para dibujar una imagen, use la función miembro [CImageList::D RAW](../mfc/reference/cimagelist-class.md#draw) . Deberá especificar un puntero a un objeto de contexto de dispositivo, el índice de la imagen que se va a dibujar, la ubicación en el contexto del dispositivo en el que se va a dibujar la imagen y un conjunto de marcas para indicar el estilo de dibujo.

Al especificar el estilo **ILD_TRANSPARENT** , `Draw` usa un proceso de dos pasos para dibujar una imagen enmascarada. En primer lugar, realiza una operación AND lógica en los bits de la imagen y los bits de la máscara. A continuación, realiza una operación XOR lógica sobre los resultados de la primera operación y los bits de fondo del contexto del dispositivo de destino. Este proceso crea áreas transparentes en la imagen resultante; es decir, cada bit en blanco de la máscara hace que el bit correspondiente de la imagen resultante sea transparente.

Antes de dibujar una imagen enmascarada en un fondo de color sólido, debe usar la función miembro [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) para establecer el color de fondo de la lista de imágenes en el mismo color que el destino. La configuración del color elimina la necesidad de crear áreas transparentes en la imagen `Draw` y permite simplemente copiar la imagen en el contexto del dispositivo de destino, lo que da lugar a un aumento significativo del rendimiento. Para dibujar la imagen, especifique el estilo **ILD_NORMAL** cuando llame a `Draw`.

Puede establecer el color de fondo de una lista de imágenes enmascaradas ([CImageList](../mfc/reference/cimagelist-class.md)) en cualquier momento para que se dibuje correctamente en cualquier fondo sólido. Al establecer el color de fondo en **CLR_NONE** , las imágenes se dibujan de manera transparente de forma predeterminada. Para recuperar el color de fondo de una lista de imágenes, use la función miembro [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) .

Los estilos **ILD_BLEND25** y **ILD_BLEND50** interpolan la imagen con el color de resaltado del sistema. Estos estilos son útiles si usa una imagen enmascarada para representar un objeto que el usuario puede seleccionar. Por ejemplo, puede usar el estilo **ILD_BLEND50** para dibujar la imagen cuando el usuario la selecciona.

Una imagen no enmascarada se copia en el contexto del dispositivo de destino `SRCCOPY` usando la operación de trama. Los colores de la imagen aparecen igual independientemente del color de fondo del contexto del dispositivo. Los estilos de dibujo especificados en `Draw` también no tienen ningún efecto en la apariencia de una imagen no enmascarada.

Además de la función miembro Draw, otra función, [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), amplía la capacidad de representar una imagen. `DrawIndirect`toma como parámetro una estructura [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) . Esta estructura se puede usar para personalizar la representación de la imagen actual, incluido el uso de códigos de operación de trama (ROP). Para obtener más información sobre los códigos ROP, vea [códigos de operación de trama](/windows/win32/gdi/raster-operation-codes) y mapas de [bits como pinceles](/windows/win32/gdi/bitmaps-as-brushes) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)
