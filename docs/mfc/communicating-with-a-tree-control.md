---
title: Comunicar con un control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: 920608724ebb362b91efdcb3eab50b80acd20474
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289889"
---
# <a name="communicating-with-a-tree-control"></a>Comunicar con un control de árbol

Usar varios métodos para llamar a funciones miembro un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto dependiendo de cómo se creó el objeto:

- Si el control de árbol está en un cuadro de diálogo, use una variable de miembro de tipo `CTreeCtrl` creados en la clase de cuadro de diálogo.

- Si el control de árbol es una ventana secundaria, use la `CTreeCtrl` objeto (o puntero) utilizado para construir el objeto.

- Si usas un `CTreeView` objeto, utilice la función [CTreeView:: GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) para obtener una referencia al control de árbol. Puede inicializar otra referencia con este valor o asignar la dirección de la referencia a un `CTreeCtrl` puntero.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
