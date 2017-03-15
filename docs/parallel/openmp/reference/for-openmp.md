---
title: "for (OpenMP) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "for"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for OpenMP directive"
ms.assetid: 8b54e034-9db2-4c1a-a2b1-72e14e930506
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# for (OpenMP)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Hace que el trabajo realizado en un bucle for dentro de una región paralela que se va a dividir entre los subprocesos.  
  
## Sintaxis  
  
```  
#pragma omp [parallel] for [clauses]  
   for_statement  
```  
  
## Comentarios  
 donde  
  
 `clause` \(opcional\)  
 cero o más cláusula.  Vea la sección comentarios para obtener una lista de las cláusulas admitidas por el párrafo.  
  
 `for_statement`  
 Un bucle for.  El comportamiento indefinido se producirá si el código de usuario de para el bucle cambia la variable de índice.  
  
## Comentarios  
 La directiva de **Para** admite las siguientes cláusulas de OpenMP:  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [lastprivate](../../../parallel/openmp/reference/lastprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [consultar](../../../parallel/openmp/reference/ordered-openmp-directives.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [informe detallado](../../../parallel/openmp/reference/reduction.md)  
  
-   [programación](../../../parallel/openmp/reference/schedule.md)  
  
 si **Paralelo** también se especifica, `clause` puede ser cualquier cláusula aceptada por las directivas de **Paralelo** o de **Para** , excepto **nowait**.  
  
 Para obtener más información, vea [2.4.1 para la construcción](../../../parallel/openmp/2-4-1-for-construct.md).  
  
## Ejemplo  
  
```  
// omp_for.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <math.h>  
#include <omp.h>  
  
#define NUM_THREADS 4  
#define NUM_START 1  
#define NUM_END 10  
  
int main() {  
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;  
   int nThreads = 0, nTmp = nStart + nEnd;  
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *   
                               unsigned(abs(nTmp))) / 2;  
   int nSumCalc = uTmp;  
  
   if (nTmp < 0)  
      nSumCalc = -nSumCalc;  
  
   omp_set_num_threads(NUM_THREADS);  
  
   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)  
   {  
      #pragma omp master  
      nThreads = omp_get_num_threads();  
  
      #pragma omp for  
      for (i=nStart; i<=nEnd; ++i) {  
            #pragma omp atomic  
            nSum += i;  
      }  
   }  
  
   if  (nThreads == NUM_THREADS) {  
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);  
      nRet = 0;  
   }  
   else {  
      printf_s("Expected %d OpenMP threads, but %d were used.\n",  
               NUM_THREADS, nThreads);  
      nRet = 1;  
   }  
  
   if (nSum != nSumCalc) {  
      printf_s("The sum of %d through %d should be %d, "  
               "but %d was reported!\n",  
               NUM_START, NUM_END, nSumCalc, nSum);  
      nRet = 1;  
   }  
   else  
      printf_s("The sum of %d through %d is %d\n",  
               NUM_START, NUM_END, nSum);  
}  
```  
  
  **4 Subprocesos de OpenMP utilizados.  la suma de 1 a 10 es 55**    
## Vea también  
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)