---
title: Actualizar una columna cuando otra tabla contiene una referencia a la fila
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 95cddfd5f030c7bd8d1220cf040de4bc5a883226
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209487"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Actualizar una columna cuando otra tabla contiene una referencia a la fila

Algunos proveedores pueden detectar qué columnas de la fila cambian, pero muchos proveedores no. Como resultado, la actualización de una columna puede producir un error cuando hay una referencia a la fila que está intentando actualizar. Para solucionar este problema, cree un descriptor de acceso independiente que contenga solo las columnas que desee cambiar. Pase el número de este descriptor de acceso a `SetData`.

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
