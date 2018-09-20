---
title: Arrastrar imágenes de una lista de imágenes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb872cba298d6d18ab5287a285b22d2f568fa04b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382380"
---
# <a name="dragging-images-from-an-image-list"></a>Arrastrar imágenes de una lista de imágenes

[CImageList](../mfc/reference/cimagelist-class.md) incluye funciones para arrastrar una imagen en la pantalla. Las funciones de arrastre mover sin problemas, una imagen en color y sin ningún intermitencia del cursor. Se pueden arrastrar imágenes enmascaradas y sin máscara.

El [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) función miembro comienza una operación de arrastre. Los parámetros incluyen el índice de la imagen de arrastre y la ubicación de la zona activa dentro de la imagen. La zona activa es un único píxel que reconocen las funciones de arrastre como la ubicación exacta en pantalla de la imagen. Normalmente, una aplicación establece la zona activa de forma que coincide con la zona activa del cursor del mouse. El [DragMove](../mfc/reference/cimagelist-class.md#dragmove) función miembro mueve la imagen a una nueva ubicación.

El [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) función miembro establece la posición inicial de la imagen de arrastre dentro de una ventana y dibuja la imagen en la posición. Los parámetros incluyen un puntero a la ventana en la que se va a dibujar la imagen y un punto que especifica las coordenadas de la posición inicial dentro de la ventana. Las coordenadas son en relación con la esquina superior izquierda de la ventana, no en el área de cliente. Lo mismo puede decirse de todas las funciones de arrastrar a la imagen que toman coordenadas como parámetros. Esto significa que debe compensar los anchos de los elementos de ventana, como el borde, la barra de título y la barra de menús, al especificar las coordenadas. Si especifica un **NULL** identificador de ventana al llamar a `DragEnter`, las funciones de arrastre dibujan la imagen en el contexto de dispositivo asociado a la ventana de escritorio y las coordenadas son relativas a la esquina superior izquierda de la pantalla.

`DragEnter` bloquea todas las demás actualizaciones a la ventana especificada durante la operación de arrastre. Si tiene que hacer ningún dibujo durante una operación de arrastre, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada utilizando la [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) función miembro. También puede usar el [función miembro DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) función miembro.

Llame a [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) cuando haya terminado arrastrar la imagen.

El [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) función miembro crea una nueva imagen de arrastre combinando la imagen especificada (normalmente una imagen del cursor del mouse) con la imagen de arrastre actual. Dado que las funciones de arrastre usan la nueva imagen durante una operación de arrastre, debe usar el Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor) función para ocultar el cursor del mouse real después de llamar a `SetDragCursorImage`. En caso contrario, el sistema puede parecer que tiene dos cursores del mouse para la duración de la operación de arrastre.

Cuando una aplicación llama `BeginDrag`, el sistema crea una lista de imágenes temporal, interno y copias especificados arrastre la imagen a la lista interna. Puede recuperar un puntero a la lista de imágenes de arrastre temporal mediante el [función miembro GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) función miembro. La función también recupera la posición actual de arrastre y el desplazamiento de la imagen de arrastre en relación con la posición de arrastre.

## <a name="see-also"></a>Vea también

[Uso de CImageList](../mfc/using-cimagelist.md)<br/>
[Controles](../mfc/controls-mfc.md)

