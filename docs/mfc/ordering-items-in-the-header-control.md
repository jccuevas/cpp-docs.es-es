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
ms.openlocfilehash: aac3c9ba284abc634af2fbeb25633b812e07f926
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928575"
---
# <a name="ordering-items-in-the-header-control"></a>Ordenar elementos en el control de encabezado
Una vez que se haya [agrega elementos a un control de encabezado](../mfc/adding-items-to-the-header-control.md), puede manipular u obtener información sobre su orden con las siguientes funciones:  
  
-   [CHeaderCtrl:: GetOrderArray](../mfc/reference/cheaderctrl-class.md#getorderarray) y [CHeaderCtrl:: SetOrderArray](../mfc/reference/cheaderctrl-class.md#setorderarray)  
  
     Recupera y establece el orden de izquierda a derecha de los elementos de encabezado.  
  
-   [CHeaderCtrl::OrderToIndex](../mfc/reference/cheaderctrl-class.md#ordertoindex).  
  
     Recupera el valor de índice de un elemento de encabezado específico.  
  
 Además de las funciones de miembro anterior, el estilo HDS_DRAGDROP permite al usuario arrastrar y colocar elementos de encabezado dentro del control de encabezado. Para obtener más información, consulte [proporciona compatibilidad con arrastrar y colocar elementos de encabezado](../mfc/providing-drag-and-drop-support-for-header-items.md).  
  
## <a name="see-also"></a>Vea también  
 [Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

