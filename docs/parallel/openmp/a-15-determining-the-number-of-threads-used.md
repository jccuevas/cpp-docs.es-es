---
title: A.15 determinar el número de subprocesos usados | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 026bb59a-f668-40db-a7cb-69a1bae83d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b50858a3384fa5f8d867f13a699e1fc271c101ef
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686391"
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