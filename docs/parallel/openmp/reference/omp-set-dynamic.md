---
title: "omp_set_dynamic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_dynamic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_dynamic OpenMP function"
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_set_dynamic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Indica que el número de subprocesos disponibles en la región paralela subsiguiente se puede ajustar el motor en tiempo de ejecución.  
  
## Sintaxis  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## Comentarios  
 donde  
  
 `val`  
 Un valor que indica si el número de subprocesos disponibles en la región paralela subsiguiente se puede ajustar el motor en tiempo de ejecución.  Si es distinto de cero, el runtime puede ajustar el número de subprocesos, si cero, el runtime no ajusta dinámicamente el número de subprocesos.  
  
## Comentarios  
 el número de subprocesos nunca superará el valor establecido por [omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md) o por [OMP\_NUM\_THREADS](../../../parallel/openmp/reference/omp-num-threads.md).  
  
 Utilice [omp\_get\_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md) para mostrar la configuración actual de `omp_set_dynamic`.  
  
 El valor de `omp_set_dynamic` reemplazará el valor de la variable de entorno [OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md) .  
  
 Para obtener más información, vea [3.1.7 omp\_set\_dynamic Function](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).  
  
## Ejemplo  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
  **1**  
**1**   
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)