---
title: "atomic | Microsoft Docs"
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
  - "atomic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atomic OpenMP directive"
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# atomic
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Especifica que una ubicación de memoria que se actualizará atómico.  
  
## Sintaxis  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### Parámetros  
 `expression`  
 La instrucción que contiene la ubicación de memoria de valor l cuya que desea proteger contra escribe varias.  Para obtener más información sobre las formas de la expresión válida, vea la especificación de OpenMP.  
  
## Comentarios  
 la directiva de `atomic` no admite ninguna cláusula de OpenMP.  
  
 Para obtener más información, vea [2.6.4 atomic Construct](../../../parallel/openmp/2-6-4-atomic-construct.md).  
  
## Ejemplo  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
  **número de subprocesos: 10**   
## Vea también  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)