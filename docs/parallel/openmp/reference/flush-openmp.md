---
title: Flush (OpenMP) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Flush
dev_langs: C++
helpviewer_keywords: flush OpenMP directive
ms.assetid: 150ca46e-d4f7-4423-b0a4-838df40aeb67
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 72b69daf431ab9dfd2b5c2ed7cebdc8c5af75847
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="flush-openmp"></a>flush (OpenMP)
Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#pragma omp flush [(var)]  
```  
  
## <a name="remarks"></a>Comentarios  
 donde,  
  
 `var` (opcional)  
 Una lista separada por comas de variables que representan los objetos que desea sincronizar. Si `var` no se especifica, toda la memoria se vacía.  
  
## <a name="remarks"></a>Comentarios  
 El **vaciar** directiva es compatible con ningún cláusulas de OpenMP.  
  
 Para obtener más información, consulte [2.6.5 flush (directiva)](../../../parallel/openmp/2-6-5-flush-directive.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// omp_flush.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
void read(int *data) {  
   printf_s("read data\n");  
   *data = 1;  
}  
  
void process(int *data) {  
   printf_s("process data\n");  
   (*data)++;  
}  
  
int main() {  
   int data;  
   int flag;  
  
   flag = 0;  
  
   #pragma omp parallel sections num_threads(2)  
   {  
      #pragma omp section  
      {  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         read(&data);  
         #pragma omp flush(data)  
         flag = 1;  
         #pragma omp flush(flag)  
         // Do more work.  
      }  
  
      #pragma omp section   
      {  
         while (!flag) {  
            #pragma omp flush(flag)  
         }  
         #pragma omp flush(data)  
  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         process(&data);  
         printf_s("data = %d\n", data);  
      }  
   }  
}  
```  
  
```Output  
Thread 0: read data  
Thread 1: process data  
data = 2  
```  
  
## <a name="see-also"></a>Vea también  
 [Directivas](../../../parallel/openmp/reference/openmp-directives.md)