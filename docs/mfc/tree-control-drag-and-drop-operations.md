---
title: "Las operaciones de arrastrar y colocar del Control de árbol | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], drag and drop operations
- drag and drop [MFC], CTreeCtrl
- tree controls [MFC], drag and drop operations
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 978c577a01b2f574009c601ca594a235e0712d71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-drag-and-drop-operations"></a>Operaciones de arrastrar y colocar del control de árbol
Un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía una notificación cuando el usuario empieza a arrastrar un elemento. El control envía un [TVN_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) recibe un mensaje de notificación cuando el usuario comienza a arrastrar un elemento con el botón primario del mouse y un [TVN_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) recibe un mensaje de notificación cuando el usuario comienza a arrastrar con el botón derecho. Puede impedir que un control de árbol enviar estas notificaciones proporcionando el control de árbol el **TVS_DISABLEDRAGDROP** estilo.  
  
 Obtener una imagen que se mostrará durante una operación de arrastre mediante una llamada a la [función miembro CreateDragImage](../mfc/reference/ctreectrl-class.md#createdragimage) función miembro. El control de árbol crea un mapa de bits de arrastre basado en la etiqueta del elemento que se están arrastrando. A continuación, el control de árbol crea una lista de imágenes, agrega el mapa de bits y devuelve un puntero a la [CImageList](../mfc/reference/cimagelist-class.md) objeto.  
  
 Debe proporcionar el código que realmente se arrastra el elemento. Esto suele implica utilizando las capacidades de arrastre de las funciones de la lista de imágenes y procesar la [WM_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) y [WM_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) (o [WM_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)) mensajes enviados después de que ha comenzado la operación de arrastre. Para obtener más información acerca de las funciones de la lista de imágenes, vea [CImageList](../mfc/reference/cimagelist-class.md) en el *referencia de MFC* y [listas de imágenes](http://msdn.microsoft.com/library/windows/desktop/bb761389) del SDK de Windows. Para obtener más información acerca de cómo arrastrar un elemento de control de árbol, vea [arrastrar el elemento de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb760017), también en el [!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)].  
  
 Si hay elementos en un control de árbol ser el destino de una operación de arrastrar y colocar, debe saber el momento en el cursor del mouse está sobre un elemento de destino. Puede averiguar mediante una llamada a la [HitTest](../mfc/reference/ctreectrl-class.md#hittest) función miembro. Especifique un punto y un entero o la dirección de un [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) estructura que contiene las coordenadas del cursor del mouse actuales. La función devuelve el entero o la estructura contiene una marca que indica la ubicación del cursor del mouse en relación con el control de árbol. Si el cursor está sobre un elemento en el control de árbol, la estructura contiene el identificador del elemento así.  
  
 Puede indicar que el elemento es el destino de una operación de arrastrar y colocar llamando a la [SetItem](../mfc/reference/ctreectrl-class.md#setitem) función de miembro para establecer el estado en el `TVIS_DROPHILITED` valor. Un elemento que tenga este estado se dibuja en el estilo que se usa para indicar un destino de arrastrar y colocar.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

