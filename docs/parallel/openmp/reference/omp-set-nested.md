---
title: "omp_set_nested | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_set_nested"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_set_nested OpenMP function"
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# omp_set_nested
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Paralelismo anidado de permisos.  
  
## Sintaxis  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## Comentarios  
 donde  
  
 `val`  
 Si es distinto de cero, los permisos anidados paralelismo.  Si cero, deshabilita paralelismo anidados.  
  
## Comentarios  
 El paralelismo anidados OMP se puede convertir con `omp_set_nested`, o estableciendo la variable de entorno [OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md) .  
  
 El valor de `omp_set_nested` reemplazará el valor de la variable de entorno `OMP_NESTED` .  
  
 Cuando está habilitada, la variable de entorno puede interrumpir un programa de otro modo operativo porque el número de subprocesos aumenta exponencialmente al anidar regiones paralelas.  Como una función de que el tal forma que 6 medir el tiempo con el número de subprocesos de OMP establecidos en 4 requiere 4.096 \(4 a la potencia 6\) de los subprocesos En General, que el rendimiento de la aplicación degradará si el número de subproceso supera el número de procesadores.  una excepción a esto sería aplicaciones enlazadas E\/S.  
  
 Utilice [omp\_get\_nested](../../../parallel/openmp/reference/omp-get-nested.md) para mostrar la configuración actual de `omp_set_nested`.  
  
 Para obtener más información, vea [3.1.9 omp\_set\_nested Function](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).  
  
## Ejemplo  
  
```  
// omp_set_nested.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_nested(1);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_nested( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_nested( ));  
        }  
}  
```  
  
  **1**  
**1**   
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)