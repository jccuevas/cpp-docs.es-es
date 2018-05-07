---
title: Ordenar elementos en el Control de encabezado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DS_DRAGDROP
dev_langs:
- C++
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dfa84326286b03f3ed0154138ed7f847440df284
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="ordering-items-in-the-header-control"></a>Ordenar elementos en el control de encabezado
Una vez que se haya [agrega elementos a un control de encabezado](../mfc/adding-items-to-the-header-control.md), puede manipular u obtener información sobre su orden con las siguientes funciones:  
  
-   [CHeaderCtrl:: GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) y [CHeaderCtrl:: SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)  
  
     Recupera y establece el orden de izquierda a derecha de los elementos de encabezado.  
  
-   [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).  
  
     Recupera el valor de índice de un elemento de encabezado específico.  
  
 Además de las funciones de miembro anterior, el `HDS_DRAGDROP` estilo permite al usuario arrastrar y colocar elementos de encabezado dentro del control de encabezado. Para obtener más información, consulte [proporciona compatibilidad con arrastrar y colocar elementos de encabezado](../mfc/providing-drag-and-drop-support-for-header-items.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

