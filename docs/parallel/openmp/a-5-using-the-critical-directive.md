---
title: "Mediante la directiva crítica de A.5 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 14423018-25b9-4f98-92f2-34c9b0ac0ce0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ef678b58df9d2c323cdebb61feed52ebbaf607f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="a5---using-the-critical-directive"></a>A.5 Usar la directiva critical
En el ejemplo siguiente se incluye varios `critical` directivas ([sección 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) en la página 18). El ejemplo muestra un modelo de puesta en cola en el que se quita de la cola y trabajada en una tarea. Para protegerse de la misma tarea de eliminación de la cola de varios subprocesos, la operación de eliminación de cola debe estar en un `critical` sección. Dado que las dos colas en este ejemplo son independientes, están protegidos por `critical` directivas con nombres diferentes, *xaxis* y *eje y*.  
  
```  
#pragma omp parallel shared(x, y) private(x_next, y_next)  
{  
    #pragma omp critical ( xaxis )  
        x_next = dequeue(x);  
    work(x_next);  
    #pragma omp critical ( yaxis )  
        y_next = dequeue(y);  
    work(y_next);  
}  
```