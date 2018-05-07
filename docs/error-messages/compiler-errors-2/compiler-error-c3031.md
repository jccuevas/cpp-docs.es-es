---
title: Error del compilador C3031 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3031
dev_langs:
- C++
helpviewer_keywords:
- C3031
ms.assetid: 7e621e7e-eda7-45b5-8836-29599cd05255
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f2508523c8cba570192ebcbe4f8e3cd29b6cce8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3031"></a>Error del compilador C3031
'var': la variable de la cláusula 'reduction' debe tener un tipo aritmético escalar  
  
 Se pasó una variable de tipo incorrecto a una cláusula reduction.  
  
 El ejemplo siguiente genera la advertencia C3031:  
  
```  
// C3031.cpp  
// compile with: /openmp /link vcomps.lib  
#include <stdio.h>  
#include "omp.h"  
  
typedef struct {  
   int n;  
} Incomplete;  
  
extern Incomplete inc;  
int i = 9;  
  
int main() {  
   #pragma omp parallel reduction(+: inc)   // C3031   
      ;  
  
   #pragma omp parallel reduction(+: i)     // OK  
      ;  
}  
```