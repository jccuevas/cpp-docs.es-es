---
title: Comunicar con un control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: a5749b76468a7ba30cd48dc3a9b61f2de7ac67b9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654195"
---
# <a name="communicating-with-a-tree-control"></a>Comunicar con un control de árbol

Usar varios métodos para llamar a funciones miembro un [CTreeCtrl](../mfc/reference/ctreectrl-class.md) objeto dependiendo de cómo se creó el objeto:

- Si el control de árbol está en un cuadro de diálogo, use una variable de miembro de tipo `CTreeCtrl` creados en la clase de cuadro de diálogo.

- Si el control de árbol es una ventana secundaria, use la `CTreeCtrl` objeto (o puntero) utilizado para construir el objeto.

- Si usas un `CTreeView` objeto, utilice la función [CTreeView:: GetTreeCtrl](../mfc/reference/ctreeview-class.md#gettreectrl) para obtener una referencia al control de árbol. Puede inicializar otra referencia con este valor o asignar la dirección de la referencia a un `CTreeCtrl` puntero.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

