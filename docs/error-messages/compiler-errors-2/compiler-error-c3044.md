---
title: Error del compilador C3044 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3044
dev_langs:
- C++
helpviewer_keywords:
- C3044
ms.assetid: 9f3e25b2-4676-49ab-97bf-6c88cd0fa377
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61021438711544bb9e6489855f8bcb46a867a1d4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3044"></a>Error del compilador C3044
'section' : solamente se permite si se anida directamente bajo una directiva 'sections' de OpenMP  
  
 El compilador encontró una directiva `section` que se usó incorrectamente. Para más información, vea [sections](../../parallel/openmp/reference/sections-openmp.md).  
  
 El ejemplo siguiente genera la advertencia C3044:  
  
```  
// C3044.cpp  
// compile with: /openmp /c  
#include "omp.h"  
int main() {  
   int n2 = 2, n3 = 3;  
  
   #pragma omp parallel  
   {  
      ++n2;  
  
      #pragma omp sections  
      {  
         ++n2;  
      }  
  
      #pragma omp section   // C3044  
      {  
         ++n3;  
      }  
   }  
  
   #pragma omp parallel  
   {  
      ++n2;  
  
      #pragma omp sections  
      {  
         #pragma omp section   // OK  
         {  
            ++n3;  
         }  
      }  
   }  
}  
```