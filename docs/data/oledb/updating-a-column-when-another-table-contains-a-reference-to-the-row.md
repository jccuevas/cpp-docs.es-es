---
title: Actualizar una columna cuando otra tabla contiene una referencia a la fila
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 46de5f54a3ec6525f779a6b55a700429a2a84fef
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59039220"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Actualizar una columna cuando otra tabla contiene una referencia a la fila

Algunos proveedores pueden detectar qué columnas cambian en la fila, pero muchos proveedores no. Como resultado, al actualizar una columna puede dar lugar a un error cuando hay una referencia a la fila que está intentando actualizar. Para solucionar este problema, cree un descriptor de acceso independiente que contiene solo las columnas que desea cambiar. Pase el número de descriptor de acceso a `SetData`.

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)