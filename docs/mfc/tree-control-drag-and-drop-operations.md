---
title: Las operaciones de arrastrar y colocar del Control de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e1c642642f94c021001ae67d2dcc3fd87f4f287
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589090"
---
# <a name="tree-control-drag-and-drop-operations"></a>Operaciones de arrastrar y colocar del control de árbol
Un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía una notificación cuando el usuario comienza a arrastrar un elemento. El control envía un [TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) recibe un mensaje de notificación cuando el usuario comienza a arrastrar un elemento con el botón primario del mouse y un [TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) recibe un mensaje de notificación cuando el usuario comienza a arrastrar con el botón derecho. Puede impedir que un control de árbol enviar estas notificaciones, por lo que proporciona el control de árbol el estilo TVS_DISABLEDRAGDROP.  
  
 Obtener una imagen para mostrar durante una operación de arrastre mediante una llamada a la [función miembro CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) función miembro. El control de árbol crea un mapa de bits arrastrar basado en la etiqueta del elemento que se está arrastrando. A continuación, el control de árbol crea una lista de imágenes, agrega el mapa de bits y devuelve un puntero a la [CImageList](../mfc/reference/cimagelist-class.md) objeto.  
  
 Debe proporcionar el código que realmente se arrastra el elemento. Normalmente, esto implica usar las capacidades de arrastrar de las funciones de la lista de imágenes y el procesamiento del [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) y [WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (o [WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)) mensajes enviados después de que ha comenzado la operación de arrastre. Para obtener más información acerca de las funciones de la lista de imágenes, consulte [CImageList](../mfc/reference/cimagelist-class.md) en el *referencia de MFC* y [listas de imágenes](http://msdn.microsoft.com/library/windows/desktop/bb761389) en el SDK de Windows. Para obtener más información acerca de cómo arrastrar un elemento de control de árbol, vea [arrastrar el elemento de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb760017), también en el SDK de Windows.  
  
 Si los elementos de un control de árbol que se van a ser los destinos de una operación de arrastrar y colocar, necesita saber cuándo está el cursor del mouse sobre un elemento de destino. Puede averiguar mediante una llamada a la [HitTest](../mfc/reference/ctreectrl-class.md#hittest) función miembro. Especifique un punto y un entero o la dirección de un [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) estructura que contiene las coordenadas del cursor del mouse actuales. La función que devuelve el entero o la estructura contiene una marca que indica la ubicación del cursor del mouse en relación con el control de árbol. Si el cursor está sobre un elemento en el control de árbol, la estructura contiene el identificador del elemento así.  
  
 Puede indicar que un elemento es el destino de una operación de arrastrar y colocar mediante una llamada a la [SetItem](../mfc/reference/ctreectrl-class.md#setitem) función miembro para establecer el estado en el `TVIS_DROPHILITED` valor. Un elemento que tiene este estado se dibuja con el estilo usado para indicar un destino de arrastrar y colocar.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

