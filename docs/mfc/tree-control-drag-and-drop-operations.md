---
title: Operaciones de arrastrar y colocar del control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: 5d2c5aa511844a3d7cbe64d9a15f8ffb46046b29
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510908"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operaciones de arrastrar y colocar del control de árbol

Un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía una notificación cuando el usuario empieza a arrastrar un elemento. El control envía un mensaje de notificación [TVN_BEGINDRAG](/windows/win32/Controls/tvn-begindrag) cuando el usuario comienza a arrastrar un elemento con el botón primario del mouse y un mensaje de notificación [TVN_BEGINRDRAG](/windows/win32/Controls/tvn-beginrdrag) cuando el usuario empieza a arrastrar con el botón derecho. Puede evitar que un control de árbol Envíe estas notificaciones proporcionando el estilo TVS_DISABLEDRAGDROP al control de árbol.

Para obtener una imagen y mostrarla durante una operación de arrastre, llame a la función miembro [CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) . El control de árbol crea un mapa de bits de arrastre basado en la etiqueta del elemento que se está arrastrando. Después, el control de árbol crea una lista de imágenes, le agrega el mapa de bits y devuelve un puntero al objeto [CImageList](../mfc/reference/cimagelist-class.md) .

Debe proporcionar el código que realmente arrastra el elemento. Normalmente, esto implica el uso de las funciones de arrastre de las funciones de la lista de imágenes y el procesamiento de los mensajes [WM_MOUSEMOVE](/windows/win32/inputdev/wm-mousemove) y [WM_LBUTTONUP](/windows/win32/inputdev/wm-lbuttonup) (o [WM_RBUTTONUP](/windows/win32/inputdev/wm-rbuttonup)) enviados una vez iniciada la operación de arrastre. Para obtener más información sobre las funciones de la lista de imágenes, vea [CImageList](../mfc/reference/cimagelist-class.md) en las [listas de imágenes](/windows/win32/controls/image-lists) y de referencia de *MFC* en el Windows SDK. Para obtener más información sobre cómo arrastrar un elemento de control de árbol, vea [arrastrar el elemento de vista de árbol](/windows/win32/Controls/tree-view-controls), también en el Windows SDK.

Si los elementos de un control de árbol van a ser los destinos de una operación de arrastrar y colocar, debe saber cuándo está el cursor del mouse en un elemento de destino. Puede averiguar mediante una llamada a la función miembro [HitTest](../mfc/reference/ctreectrl-class.md#hittest) . Se especifica un punto y un entero, o la dirección de una estructura [TVHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tvhittestinfo) que contiene las coordenadas actuales del cursor del mouse. Cuando la función devuelve, el entero o la estructura contiene una marca que indica la ubicación del cursor del mouse con respecto al control de árbol. Si el cursor está sobre un elemento del control de árbol, la estructura contiene también el identificador del elemento.

Puede indicar que un elemento es el destino de una operación de arrastrar y colocar mediante una llamada a la función miembro [SetItem](../mfc/reference/ctreectrl-class.md#setitem) para establecer el estado en el `TVIS_DROPHILITED` valor. Un elemento que tiene este estado se dibuja en el estilo utilizado para indicar un destino de arrastrar y colocar.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
