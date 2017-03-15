---
title: "omp_test_nest_lock | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "omp_test_nest_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "omp_test_nest_lock OpenMP function"
ms.assetid: 4c909bbe-80e0-4100-aca6-d415d7dc5294
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# omp_test_nest_lock
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Los intentos de establecer un bloqueo encajable pero no bloquean la ejecución de subprocesos.  
  
## Sintaxis  
  
```  
int omp_test_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## Comentarios  
 donde  
  
 `lock`  
 Una variable de [omp\_nest\_lock\_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) cuyas se inicializó con [omp\_init\_nest\_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md).  
  
## Comentarios  
 Para obtener más información, vea [3.2.5 omp\_test\_lock and omp\_test\_nest\_lock Functions](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).  
  
## Ejemplo  
  
```  
// omp_test_nest_lock.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
omp_nest_lock_t nestable_lock;      
  
int main() {  
   omp_init_nest_lock(&nestable_lock);  
  
   #pragma omp parallel num_threads(4)  
   {  
      int tid = omp_get_thread_num();  
      while (!omp_test_nest_lock(&nestable_lock))  
         printf_s("Thread %d - failed to acquire nestable_lock\n",  
                tid);  
  
      printf_s("Thread %d - acquired nestable_lock\n", tid);  
  
      if (omp_test_nest_lock(&nestable_lock)) {  
         printf_s("Thread %d - acquired nestable_lock again\n",  
                tid);  
         printf_s("Thread %d - released nestable_lock\n",   
                tid);  
         omp_unset_nest_lock(&nestable_lock);  
      }  
  
      printf_s("Thread %d - released nestable_lock\n", tid);  
      omp_unset_nest_lock(&nestable_lock);  
   }  
  
   omp_destroy_nest_lock(&nestable_lock);  
}  
```  
  
  **subproceso 1 \- nestable\_lock adquirido**  
**Subproceso 0 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 1 \- nestable\_lock adquirido de nuevo**  
**Subproceso 0 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 1 \- nestable\_lock liberado**  
**Subproceso 0 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 1 \- nestable\_lock liberado**  
**Subproceso 0 \- no se pudo adquirir el nestable\_lock**  
**subproceso 3 \- nestable\_lock adquirido**  
**Subproceso 0 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 3 \- nestable\_lock adquirido de nuevo**  
**Subproceso 0 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 3 \- nestable\_lock liberado**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 3 \- nestable\_lock liberado**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**subproceso 0 \- nestable\_lock adquirido**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 0 \- nestable\_lock adquirido de nuevo**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 0 \- nestable\_lock liberado**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**Subproceso 0 \- nestable\_lock liberado**  
**Subproceso 2 \- no se pudo adquirir el nestable\_lock**  
**subproceso 2 \- nestable\_lock adquirido**  
**Subproceso 2 \- nestable\_lock adquirido de nuevo**  
**Subproceso 2 \- nestable\_lock liberado**  
**Subproceso 2 \- nestable\_lock liberado**   
## Vea también  
 [Functions](../../../parallel/openmp/reference/openmp-functions.md)