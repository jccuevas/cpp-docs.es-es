---
title: Comunicar con un control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], communicating with
- CTreeCtrl class [MFC], calling member functions
- communications, tree controls
- tree controls
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
ms.openlocfilehash: f480cdad2fce53f830b8067083a8a4be4b4e4848
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619644"
---
# <a name="communicating-with-a-tree-control"></a>Comunicar con un control de árbol

Puede usar métodos diferentes para llamar a funciones miembro en un objeto [CTreeCtrl](reference/ctreectrl-class.md) en función de cómo se haya creado el objeto:

- Si el control de árbol está en un cuadro de diálogo, use una variable miembro de tipo `CTreeCtrl` que cree en la clase de cuadro de diálogo.

- Si el control de árbol es una ventana secundaria, utilice el `CTreeCtrl` objeto (o puntero) que usó para construir el objeto.

- Si está utilizando un `CTreeView` objeto, utilice la función [CTreeView:: GetTreeCtrl](reference/ctreeview-class.md#gettreectrl) para obtener una referencia al control de árbol. Puede inicializar otra referencia con este valor o asignar la dirección de la referencia a un `CTreeCtrl` puntero.

## <a name="see-also"></a>Consulte también

[Usar CTreeCtrl](using-ctreectrl.md)<br/>
[Permite](controls-mfc.md)
