---
title: "omp_get_num_procs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_get_num_procs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_num_procs OpenMP function"
ms.assetid: 14a10b8f-e59b-4211-a292-687648c9f760
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# omp_get_num_procs
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Devuelve el número de procesadores disponibles cuando se llama a la función.  
  
## Sintaxis  
  
```  
int omp_get_num_procs();  
```  
  
## Comentarios  
 Para obtener más información, vea [3.1.5 omp\_get\_num\_procs Function](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).  
  
## Ejemplo  
  
```  
// omp_get_num_procs.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    printf_s("%d\n", omp_get_num_procs( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_num_procs( ));  
        }  
}  
```  
  
  **\/\/Espera el resultado siguiente cuando el ejemplo se ejecuta en un equipo con dos procesadores:**  
**2**  
**2**   
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)