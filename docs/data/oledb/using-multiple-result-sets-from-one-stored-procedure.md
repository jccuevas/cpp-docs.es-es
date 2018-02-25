---
title: Usar varios conjuntos de resultados de un procedimiento almacenado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 39faf4313fbf4ed98810e8f9dd557897f2bfb834
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>Utilizar varios conjuntos de resultados de un procedimiento almacenado
Mayoría de los procedimientos almacenados devuelven varios conjuntos de resultados. Estos procedimientos almacenados suelen incluyen una o varias instrucciones select. El consumidor debe tener en cuenta esta opción para controlar todos los conjuntos de resultados.  
  
### <a name="to-handle-multiple-result-sets"></a>Para controlar los resultados múltiples establece  
  
1.  Crear un `CCommand` clase con `CMultipleResults` como un argumento de plantilla y el descriptor de acceso de su elección. Normalmente, se trata de un descriptor de acceso dinámico o manual. Si utiliza otro tipo de descriptor de acceso, es posible que no pueda determinar las columnas de salida para cada conjunto de filas.  
  
2.  Ejecute el procedimiento almacenado como de costumbre y enlazar las columnas (vea [¿cómo puedo recuperar datos?](../../data/oledb/fetching-data.md)).  
  
3.  Usar los datos.  
  
4.  Llame a `GetNextResult` en la `CCommand` clase. Si hay otro conjunto de filas de resultados, `GetNextResult` devuelve S_OK y debe volver a enlazar las columnas si se utiliza un descriptor de acceso manual. Si `GetNextResult` devuelve un error, no hay ningún resultado más conjuntos disponible.  
  
## <a name="see-also"></a>Vea también  
 [Usar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)