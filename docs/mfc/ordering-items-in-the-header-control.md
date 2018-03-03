---
title: Ordenar elementos en el Control de encabezado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 48adbc53ad0e4974edd86d3f8a96d74214093dda
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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

