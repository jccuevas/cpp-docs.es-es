---
title: Arrastrar imágenes de una lista de imágenes
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 3035e6f21d38568b364fce02358c3baed4870bc3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508641"
---
# <a name="dragging-images-from-an-image-list"></a>Arrastrar imágenes de una lista de imágenes

[CImageList](../mfc/reference/cimagelist-class.md) incluye funciones para arrastrar una imagen en la pantalla. Las funciones de arrastre mueven una imagen sin problemas, en color y sin intermitencia del cursor. Se pueden arrastrar imágenes enmascaradas y sin máscara.

La función miembro [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) inicia una operación de arrastre. Los parámetros incluyen el índice de la imagen que se va a arrastrar y la ubicación de la zona activa dentro de la imagen. La zona activa es un solo píxel que las funciones de arrastre reconocen como la ubicación de pantalla exacta de la imagen. Normalmente, una aplicación establece la zona activa para que coincida con la zona activa del cursor del mouse. La función miembro [DragMove](../mfc/reference/cimagelist-class.md#dragmove) mueve la imagen a una nueva ubicación.

La función miembro [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) establece la posición inicial de la imagen de arrastre dentro de una ventana y dibuja la imagen en la posición. Los parámetros incluyen un puntero a la ventana en la que se va a dibujar la imagen y un punto que especifica las coordenadas de la posición inicial dentro de la ventana. Las coordenadas son relativas a la esquina superior izquierda de la ventana, no al área cliente. Lo mismo se aplica a todas las funciones de arrastre de imagen que toman las coordenadas como parámetros. Esto significa que debe compensar el ancho de los elementos de ventana, como el borde, la barra de título y la barra de menús, al especificar las coordenadas. Si especifica un identificador de ventana **nulo** al llamar `DragEnter`a, las funciones de arrastre dibujan la imagen en el contexto de dispositivo asociado a la ventana del escritorio y las coordenadas son relativas a la esquina superior izquierda de la pantalla.

`DragEnter`bloquea todas las demás actualizaciones en la ventana determinada durante la operación de arrastre. Si necesita realizar algún dibujo durante una operación de arrastre, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada mediante la función miembro [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) . También puede usar la función miembro [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) .

Llame a [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) cuando haya terminado de arrastrar la imagen.

La función miembro [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) crea una nueva imagen de arrastre combinando la imagen especificada (normalmente una imagen de cursor del mouse) con la imagen de arrastre actual. Dado que las funciones de arrastre usan la nueva imagen durante una operación de arrastre, debe usar la función [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) de Windows para ocultar el cursor del mouse `SetDragCursorImage`real después de llamar a. De lo contrario, puede parecer que el sistema tiene dos cursores del mouse mientras dure la operación de arrastre.

Cuando una aplicación llama `BeginDrag`a, el sistema crea una lista de imágenes temporal e internas y copia la imagen de arrastre especificada en la lista interna. Puede recuperar un puntero a la lista de imágenes de arrastre temporal mediante la función miembro [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) . La función también recupera la posición de arrastre actual y el desplazamiento de la imagen de arrastre con respecto a la posición de arrastre.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)
