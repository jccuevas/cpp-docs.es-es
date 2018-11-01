---
title: Actualizar una columna cuando otra tabla contiene una referencia a la fila
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 2adca735558033aa9324f37b5a61385b5f48096c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519905"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Actualizar una columna cuando otra tabla contiene una referencia a la fila

Algunos proveedores pueden detectar qué columnas cambian en la fila, pero muchos proveedores no. Como resultado, al actualizar una columna puede dar lugar a un error cuando hay una referencia a la fila que está intentando actualizar. Para solucionar este problema, cree un descriptor de acceso independiente que contiene solo las columnas que desea cambiar. Pase el número de descriptor de acceso a `SetData`.

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)