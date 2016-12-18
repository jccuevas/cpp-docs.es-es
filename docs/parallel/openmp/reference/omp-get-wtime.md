---
title: "omp_get_wtime | Microsoft Docs"
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
  - "omp_get_wtime"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_get_wtime OpenMP function"
ms.assetid: c8dee105-ec1b-42e5-a6e3-edeedcf9854c
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# omp_get_wtime
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Devuelve un valor en segundos de tiempo transcurrido de algún punto.  
  
## Sintaxis  
  
```  
double omp_get_wtime( );  
```  
  
## Valor devuelto  
 Devuelve un valor en segundos de tiempo transcurrido de algún punto arbitrario, pero coherente.  
  
## Comentarios  
 Ese punto permanecerá coherente durante la ejecución del programa, creando comparaciones siguientes posibles.  
  
 Para obtener más información, vea [3.3.1 omp\_get\_wtime Function](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).  
  
## Ejemplo  
  
```  
// omp_get_wtime.cpp  
// compile with: /openmp  
#include "omp.h"  
#include <stdio.h>  
#include <windows.h>  
  
int main() {  
    double start = omp_get_wtime( );  
    Sleep(1000);  
    double end = omp_get_wtime( );  
    double wtick = omp_get_wtick( );  
  
    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",  
             start, end, end - start);  
  
    printf_s("wtick = %.16g\n1/wtick = %.16g\n",  
             wtick, 1.0 / wtick);  
}  
```  
  
  **inicio \= 594255,3671159324**  
**final \= 594256,3664474116**  
**diff \= 0,9993314791936427**  
**wtick \= 2.793651148400146e\-007**  
**1\/wtick \= 3579545**   
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)