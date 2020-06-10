---
title: Ordenar elementos en el control de encabezado
ms.date: 11/04/2016
f1_keywords:
- DS_DRAGDROP
helpviewer_keywords:
- sequence [MFC]
- sequence [MFC], header control items
- OrderToIndex method [MFC]
- DS_DRAGDROP notification [MFC]
- GetOrderArray method [MFC]
- SetOrderArray method [MFC]
- header controls [MFC], ordering items
ms.assetid: 5aaef872-75b5-49c5-8fed-6f9a81fca812
ms.openlocfilehash: c4b4711729c6c3a4b63d4ad05252a5c49df98a0c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622135"
---
# <a name="ordering-items-in-the-header-control"></a>Ordenar elementos en el control de encabezado

Una vez que haya [agregado elementos a un control de encabezado](adding-items-to-the-header-control.md), puede manipular u obtener información sobre su pedido con las siguientes funciones:

- [CHeaderCtrl:: GetOrderArray](reference/cheaderctrl-class.md#getorderarray) y [CHeaderCtrl:: SetOrderArray](reference/cheaderctrl-class.md#setorderarray)

   Recupera y establece el orden de izquierda a derecha de los elementos de encabezado.

- [CHeaderCtrl:: OrderToIndex](reference/cheaderctrl-class.md#ordertoindex).

   Recupera el valor de índice de un elemento de encabezado específico.

Además de las funciones miembro anteriores, el estilo de HDS_DRAGDROP permite al usuario arrastrar y colocar elementos de encabezado dentro del control de encabezado. Para obtener más información, vea [proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado](providing-drag-and-drop-support-for-header-items.md).

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](using-cheaderctrl.md)
