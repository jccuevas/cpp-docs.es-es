---
title: Usar varios conjuntos de resultados de un procedimiento almacenado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ec887f01e377ffa6295086bbeeb56dcd884d6276
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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