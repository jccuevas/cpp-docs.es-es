---
title: Actualizar una columna cuando otra tabla contiene una referencia a la fila | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4c5fdf37cedd2c20430f87e15446244321c68bdf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Actualizar una columna cuando otra tabla contiene una referencia a la fila
Algunos proveedores pueden detectar qué columnas cambian en la fila, pero no de muchos proveedores. Como resultado, actualizar una columna puede producir un error cuando no hay una referencia a la fila que está intentando actualizar. Para solucionar este problema, cree un descriptor de acceso independiente que contiene solo las columnas que desea cambiar. Pase el número del descriptor de acceso a `SetData`.  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)