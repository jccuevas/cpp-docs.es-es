---
title: Información general de los Estados de elemento de Control de árbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be5c0d3e477103edaf31bafed01265a509e48ad1
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198346"
---
# <a name="tree-control-item-states-overview"></a>Información general sobre los estados de los elementos de control de árbol
Cada elemento de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) tiene un estado actual. Por ejemplo, se puede seleccionar un elemento, deshabilitado, expandida y así sucesivamente. En su mayor parte, el control de árbol establece automáticamente el estado de un elemento para reflejar las acciones del usuario, como la selección de un elemento. Sin embargo, también puede establecer el estado de un elemento mediante el [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) función miembro y recuperar el estado actual de un elemento mediante el uso de la [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) función miembro. Para obtener una lista completa de los Estados del elemento, vea [constantes del Control de vista de árbol](/windows/desktop/Controls/tree-view-control-item-states) en el SDK de Windows.  
  
 Estado actual de un elemento especificado por el *nState* parámetro. Un control de árbol puede cambiar el estado de un elemento para reflejar una acción del usuario, por ejemplo, si selecciona el elemento o establecer el foco al elemento. Además, una aplicación podría cambiar el estado de un elemento para deshabilitar u ocultar el elemento o para especificar una imagen de estado o la imagen de superposición.  
  
 Al especificar o cambiar el estado de un elemento, el *nStateMask* parámetro especifica el estado de bits para establecer y el *nState* parámetro contiene los nuevos valores para esos bits. Por ejemplo, en el ejemplo siguiente se cambia el estado actual de un elemento primario (especificado por *hParentItem*) en un `CTreeCtrl` objeto (`m_treeCtrl`) a `TVIS_EXPANDPARTIAL`:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]  
  
 Otro ejemplo de cambio de estado sería establecer la imagen de superposición de un elemento. Para lograr esto, *nStateMask* debe incluir el `TVIS_OVERLAYMASK` valor, y *nState* debe incluir el índice basado en uno de la imagen de superposición desplazado a la izquierda ocho bits utilizando el [ Macro INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) macro. El índice puede ser 0 para no especificar ninguna imagen de superposición. La imagen de superposición debe se agregaron a la lista del control de árbol de imágenes superpuestas mediante una llamada anterior a la [función CImageList:: SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) función. La función especifica el índice basado en uno de la imagen para agregar; Este es el índice utilizado con la macro INDEXTOOVERLAYMASK. Un control de árbol puede tener hasta cuatro imágenes superpuestas.  
  
 Para establecer la imagen del estado de un elemento, *nStateMask* debe incluir el `TVIS_STATEIMAGEMASK` valor, y *nState* debe incluir el índice basado en uno de la imagen del estado desplazado a la izquierda 12 bits utilizando el [ Macro INDEXTOSTATEIMAGEMASK](/windows/desktop/api/commctrl/nf-commctrl-indextostateimagemask) macro. El índice puede ser 0 para no especificar ninguna imagen de estado. Para obtener más información acerca de las imágenes de superposición y estado, consulte [listas de imágenes de Control de árbol](../mfc/tree-control-image-lists.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

