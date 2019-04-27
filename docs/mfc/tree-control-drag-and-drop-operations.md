---
title: Operaciones de arrastrar y colocar del control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
ms.openlocfilehash: c7febeec513d8004df2bd1cc42e4e97e027e9f17
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167704"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operaciones de arrastrar y colocar del control de árbol

Un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía una notificación cuando el usuario comienza a arrastrar un elemento. El control envía un [TVN_BEGINDRAG](/windows/desktop/Controls/tvn-begindrag) recibe un mensaje de notificación cuando el usuario comienza a arrastrar un elemento con el botón primario del mouse y un [TVN_BEGINRDRAG](/windows/desktop/Controls/tvn-beginrdrag) recibe un mensaje de notificación cuando el usuario comienza a arrastrar con el botón derecho. Puede impedir que un control de árbol enviar estas notificaciones, por lo que proporciona el control de árbol el estilo TVS_DISABLEDRAGDROP.

Obtener una imagen para mostrar durante una operación de arrastre mediante una llamada a la [función miembro CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) función miembro. El control de árbol crea un mapa de bits arrastrar basado en la etiqueta del elemento que se está arrastrando. A continuación, el control de árbol crea una lista de imágenes, agrega el mapa de bits y devuelve un puntero a la [CImageList](../mfc/reference/cimagelist-class.md) objeto.

Debe proporcionar el código que realmente se arrastra el elemento. Normalmente, esto implica usar las capacidades de arrastrar de las funciones de la lista de imágenes y el procesamiento del [WM_MOUSEMOVE](/windows/desktop/inputdev/wm-mousemove) y [WM_LBUTTONUP](/windows/desktop/inputdev/wm-lbuttonup) (o [WM_RBUTTONUP](/windows/desktop/inputdev/wm-rbuttonup)) mensajes enviados después de que ha comenzado la operación de arrastre. Para obtener más información acerca de las funciones de la lista de imágenes, consulte [CImageList](../mfc/reference/cimagelist-class.md) en el *referencia de MFC* y [listas de imágenes](/windows/desktop/controls/image-lists) en el SDK de Windows. Para obtener más información acerca de cómo arrastrar un elemento de control de árbol, vea [arrastrar el elemento de vista de árbol](/windows/desktop/Controls/tree-view-controls), también en el SDK de Windows.

Si los elementos de un control de árbol que se van a ser los destinos de una operación de arrastrar y colocar, necesita saber cuándo está el cursor del mouse sobre un elemento de destino. Puede averiguar mediante una llamada a la [HitTest](../mfc/reference/ctreectrl-class.md#hittest) función miembro. Especifique un punto y un entero o la dirección de un [TVHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvhittestinfo) estructura que contiene las coordenadas del cursor del mouse actuales. La función que devuelve el entero o la estructura contiene una marca que indica la ubicación del cursor del mouse en relación con el control de árbol. Si el cursor está sobre un elemento en el control de árbol, la estructura contiene el identificador del elemento así.

Puede indicar que un elemento es el destino de una operación de arrastrar y colocar mediante una llamada a la [SetItem](../mfc/reference/ctreectrl-class.md#setitem) función miembro para establecer el estado en el `TVIS_DROPHILITED` valor. Un elemento que tiene este estado se dibuja con el estilo usado para indicar un destino de arrastrar y colocar.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
