---
title: "A.15 determinar el número de subprocesos usados | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e8b7fb8cf6218863287d582a097cb43b399cff07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="a15---determining-the-number-of-threads-used"></a>A.15 Determinar el número de subprocesos utilizados
Tenga en cuenta el siguiente ejemplo incorrecto (para [sección 3.1.2](../../parallel/openmp/3-1-2-omp-get-num-threads-function.md) en página 37):  
  
```  
np = omp_get_num_threads(); // misplaced   
#pragma omp parallel for schedule(static)  
    for (i=0; i<np; i++)  
        work(i);  
```  
  
 El `omp_get_num_threads()` call devuelve 1 en la sección de serie del código, por lo que *np* siempre será igual a 1 en el ejemplo anterior. Para determinar el número de subprocesos que se va a implementar para la región paralela, la llamada debe estar dentro de la región paralela.  
  
 En el ejemplo siguiente se muestra cómo volver a escribir este programa sin necesidad de incluir una consulta para el número de subprocesos:  
  
```  
#pragma omp parallel private(i)  
{  
    i = omp_get_thread_num();  
    work(i);  
}  
```