---
title: "copyprivate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "copyprivate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "copyprivate OpenMP clause"
ms.assetid: 02c0209d-abe8-4797-8365-a82b53c3f15d
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# copyprivate
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

especifica que una o más variables se deben compartir entre todos los subprocesos.  
  
## Sintaxis  
  
```  
copyprivate(var)  
```  
  
## Comentarios  
 donde  
  
 `var`  
 una o más variables a compartir.  Si se especifica más de una variable, los nombres de variable separados por una coma.  
  
## Comentarios  
 `copyprivate` se aplica a la directiva de [single](../../../parallel/openmp/reference/single.md) .  
  
 Para obtener más información, vea [2.7.2.8 copyprivate](../Topic/2.7.2.8%20copyprivate.md).  
  
## Ejemplo  
  
```  
// omp_copyprivate.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
float x, y, fGlobal = 1.0;  
#pragma omp threadprivate(x, y)  
  
float get_float() {  
   fGlobal += 0.001;  
   return fGlobal;  
}  
  
void use_float(float f, int t) {  
   printf_s("Value = %f, thread = %d\n", f, t);  
}  
  
void CopyPrivate(float a, float b) {  
   #pragma omp single copyprivate(a, b, x, y)   
   {  
      a = get_float();  
      b = get_float();  
      x = get_float();  
      y = get_float();  
    }  
  
   use_float(a, omp_get_thread_num());     
   use_float(b, omp_get_thread_num());     
   use_float(x, omp_get_thread_num());  
   use_float(y, omp_get_thread_num());  
}  
  
int main() {  
   float a = 9.99, b = 123.456;  
  
   printf_s("call CopyPrivate from a single thread\n");  
   CopyPrivate(9.99, 123.456);  
  
   printf_s("call CopyPrivate from a parallel region\n");  
   #pragma omp parallel       
   {  
      CopyPrivate(a, b);  
   }  
}  
```  
  
  **llamada CopyPrivate de un subproceso**  
**valor \= 1,001000, subproceso \= 0**  
**valor \= 1,002000, subproceso \= 0**  
**valor \= 1,003000, subproceso \= 0**  
**valor \= 1,004000, subproceso \= 0**  
**llamada CopyPrivate de una región paralela**  
**valor \= 1,005000, subproceso \= 0**  
**valor \= 1,005000, subproceso \= 1**  
**valor \= 1,006000, subproceso \= 0**  
**valor \= 1,006000, subproceso \= 1**  
**valor \= 1,007000, subproceso \= 0**  
**valor \= 1,007000, subproceso \= 1**  
**valor \= 1,008000, subproceso \= 0**  
**valor \= 1,008000, subproceso \= 1**   
## Vea también  
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)