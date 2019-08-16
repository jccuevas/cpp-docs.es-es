---
title: Posición de los elementos del control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
ms.openlocfilehash: 238cb40319d28a53592a594a72947f400720f935
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392484"
---
# <a name="tree-control-item-position"></a>Posición de los elementos del control de árbol

Posición inicial de un elemento se establece cuando el elemento se agrega al control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) mediante el uso de la `InsertItem` función miembro. La llamada de función miembro especifica el identificador del elemento primario y el identificador del elemento después del cual se insertará el nuevo elemento. El segundo identificador debe identificar un elemento secundario del elemento primario especificado o uno de estos valores: `TVI_FIRST`, `TVI_LAST`, o `TVI_SORT`.

Cuando `TVI_FIRST` o `TVI_LAST` se especifica, el control de árbol coloca el nuevo elemento al principio o al final de la lista del elemento primario dado de elementos secundarios. Cuando `TVI_SORT` se especifica, el control de árbol inserta el nuevo elemento en la lista de elementos secundarios en orden alfabético según el texto de las etiquetas de elemento.

Puede colocar la lista de un elemento primario de los elementos secundarios en orden alfabético mediante una llamada a la [función miembro SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) función miembro. Esta función incluye un parámetro que especifica si todos los niveles de elementos secundarios descendente del elemento primario especificado también se ordenan en orden alfabético.

El [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) función miembro permite ordenar los elementos secundarios en función de criterios que defina. Cuando se llama a esta función, especificar una función de devolución de llamada definido por la aplicación que puede llamar el control de árbol siempre que es necesario decidir el orden relativo de dos elementos secundarios. La función de devolución de llamada recibe dos valores definidos por la aplicación de 32 bits para los elementos que se comparan y un tercer valor de 32 bits que se especifica al llamar a `SortChildrenCB`.

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
