---
title: "A.12   Using the atomic Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: d3ba3c87-413d-4efa-8a45-8a7f28ab0164
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.12   Using the atomic Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ejemplo siguiente evita las condiciones de carrera \(actualizaciones simultáneas de un elemento *de x* por varios subprocesos\) mediante la directiva de `atomic` \([sección 2.6.4](../../parallel/openmp/2-6-4-atomic-construct.md) en la página 19\):  
  
```  
#pragma omp parallel for shared(x, y, index, n)  
    for (i=0; i<n; i++)   
    {  
        #pragma omp atomic  
            x[index[i]] += work1(i);  
        y[i] += work2(i);  
    }  
```  
  
 La ventaja de utilizar la directiva de `atomic` en este ejemplo es que permite que las actualizaciones de dos distintos elementos de x aparecen en paralelo.  Si una directiva de `critical` \([sección 2.6.2](../../parallel/openmp/2-6-2-critical-construct.md) en la página 18\) se usó en su lugar, después todas las actualizaciones a los elementos *de x* se ejecutan en serie \(sin embargo no en orden garantizado\).  
  
 Observe que la directiva de `atomic` sólo se aplica a la instrucción de c o C\+\+ inmediatamente después de ella.  Como resultado, los elementos *de la y* no se actualizan de forma atómica en este ejemplo.