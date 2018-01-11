---
title: "A.6 mediante la cláusula lastprivate | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1744787e1dfb90fa9af93db5dba4eecd600b4334
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6 Usar la cláusulas lastprivate
A veces, la ejecución correcta depende del valor que la última iteración de un bucle que se asigna a una variable. Estos programas deben enumerar todas las variables como argumentos a un `lastprivate` cláusula ([sección 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) en página 27) para que los valores de las variables son el mismo que cuando se ejecuta el bucle secuencialmente.  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 En el ejemplo anterior, el valor de `i` será igual al final de la región paralela `n-1`, como en el caso secuencial.