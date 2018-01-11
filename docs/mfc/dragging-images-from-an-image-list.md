---
title: "Arrastrar imágenes de una lista de imágenes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 792f112952493fe1ee86d52a6a235604ebee9db5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="dragging-images-from-an-image-list"></a>Arrastrar imágenes de una lista de imágenes
[CImageList](../mfc/reference/cimagelist-class.md) incluye funciones para arrastrar una imagen en la pantalla. Las funciones de arrastre mueven una imagen suavemente, en color y sin ninguna intermitencia del cursor. Se pueden arrastrar imágenes enmascaradas y sin máscara.  
  
 El [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) función miembro comienza una operación de arrastre. Los parámetros incluyen el índice de la imagen que se arrastra y la ubicación de la zona activa en la imagen. La zona activa es un único píxel que reconocen las funciones de arrastre como la ubicación exacta en pantalla de la imagen. Normalmente, una aplicación establece la zona activa de forma que coincide con la zona activa del cursor del mouse. El [DragMove](../mfc/reference/cimagelist-class.md#dragmove) función miembro mueve la imagen a una nueva ubicación.  
  
 El [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) función miembro establece la posición inicial de la imagen de arrastre dentro de una ventana y dibuja la imagen en la posición. Los parámetros incluyen un puntero a la ventana en la que se va a dibujar la imagen y un punto que especifica las coordenadas de la posición inicial dentro de la ventana. Las coordenadas son con respecto a la esquina superior izquierda de la ventana, no en el área de cliente. Lo mismo puede decirse de todas las funciones de arrastre de imágenes que admiten coordenadas como parámetros. Esto significa que se debe compensar para el ancho de los elementos de ventana, como el borde, la barra de título y la barra de menús, al especificar las coordenadas. Si especifica un **NULL** identificador de ventana al llamar a `DragEnter`, las funciones de arrastre dibujan la imagen en el contexto de dispositivo asociado a la ventana del escritorio y las coordenadas son relativas a la esquina superior izquierda de la pantalla.  
  
 `DragEnter`bloquea todas las demás actualizaciones a la ventana especificada durante la operación de arrastre. Si necesita realizar un dibujo durante una operación de arrastre, como resaltar el destino de una operación de arrastrar y colocar, puede ocultar temporalmente la imagen arrastrada utilizando la [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) función miembro. También puede usar el [función miembro DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) función miembro.  
  
 Llame a [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) cuando haya terminado arrastrar la imagen.  
  
 El [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) función miembro, crea una nueva imagen de arrastre combinando la imagen dada (normalmente una imagen del cursor del mouse) con la imagen de arrastre actual. Dado que las funciones de arrastre utilizan la nueva imagen durante una operación de arrastre, debe utilizar las ventanas [ShowCursor](http://msdn.microsoft.com/library/windows/desktop/ms648396) función para ocultar el cursor del mouse actual después de llamar a `SetDragCursorImage`. En caso contrario, puede parecer que el sistema tiene dos cursores del mouse para la duración de la operación de arrastre.  
  
 Cuando una aplicación llama `BeginDrag`, el sistema crea una lista de imágenes temporales, interno y copias especificados arrastre la imagen a la lista interna. Puede recuperar un puntero a la lista de imágenes de arrastre temporal mediante el [función miembro GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) función miembro. La función también recupera la posición de arrastre actual y el desplazamiento de la imagen de arrastre con respecto a la posición de arrastre.  
  
## <a name="see-also"></a>Vea también  
 [Usar CImageList](../mfc/using-cimagelist.md)   
 [Controles](../mfc/controls-mfc.md)

