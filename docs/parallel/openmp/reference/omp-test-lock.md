---
title: "omp_test_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_test_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_test_lock OpenMP function"
ms.assetid: 314ca85e-0749-4c16-800f-b0f36fed256d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# omp_test_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Los intentos de establecer un bloqueo pero no bloquean la ejecución de subprocesos.  
  
## Sintaxis  
  
```  
int omp_test_lock(  
   omp_lock_t *lock  
);  
```  
  
## Comentarios  
 donde  
  
 `lock`  
 Una variable de [omp\_lock\_t](../../../parallel/openmp/reference/omp-lock-t.md) cuyas se inicializó con [omp\_init\_lock](../../../parallel/openmp/reference/omp-init-lock.md).  
  
## Comentarios  
 Para obtener más información, vea [3.2.5 omp\_test\_lock and omp\_test\_nest\_lock Functions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).  
  
## Ejemplo  
  
```  
// omp_test_lock.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
omp_lock_t simple_lock;                   
  
int main() {  
    omp_init_lock(&simple_lock);  
  
    #pragma omp parallel num_threads(4)  
    {  
        int tid = omp_get_thread_num();  
  
        while (!omp_test_lock(&simple_lock))  
            printf_s("Thread %d - failed to acquire simple_lock\n",  
                     tid);  
  
        printf_s("Thread %d - acquired simple_lock\n", tid);  
  
        printf_s("Thread %d - released simple_lock\n", tid);  
        omp_unset_lock(&simple_lock);  
    }  
  
    omp_destroy_lock(&simple_lock);  
}  
```  
  
  **subproceso 1 \- simple\_lock adquirido**  
**Subproceso 1 \- simple\_lock liberado**  
**Subproceso 0 \- no se pudo adquirir el simple\_lock**  
**Subproceso 3 \- no se pudo adquirir el simple\_lock**  
**Subproceso 0 \- no se pudo adquirir el simple\_lock**  
**Subproceso 3 \- no se pudo adquirir el simple\_lock**  
**subproceso 2 \- simple\_lock adquirido**  
**Subproceso 0 \- no se pudo adquirir el simple\_lock**  
**Subproceso 3 \- no se pudo adquirir el simple\_lock**  
**Subproceso 0 \- no se pudo adquirir el simple\_lock**  
**Subproceso 3 \- no se pudo adquirir el simple\_lock**  
**Subproceso 2 \- simple\_lock liberado**  
**Subproceso 0 \- no se pudo adquirir el simple\_lock**  
**Subproceso 3 \- no se pudo adquirir el simple\_lock**  
**subproceso 0 \- simple\_lock adquirido**  
**Subproceso 3 \- no se pudo adquirir el simple\_lock**  
**Subproceso 0 \- simple\_lock liberado**  
**Subproceso 3 \- no se pudo adquirir el simple\_lock**  
**subproceso 3 \- simple\_lock adquirido**  
**Subproceso 3 \- simple\_lock liberado**   
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)