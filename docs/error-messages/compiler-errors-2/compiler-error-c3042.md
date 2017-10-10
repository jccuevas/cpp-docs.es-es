---
title: Error del compilador C3042 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3042
dev_langs:
- C++
helpviewer_keywords:
- C3042
ms.assetid: bf73f61e-5bd2-40a8-9b06-6244e6a15a41
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f0fe35a4021cca6ac1e3dd9846a3c165f50797f4
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3042"></a>Error del compilador C3042
Las cláusulas 'copyprivate' y 'nowait' no pueden aparecer juntas en la directiva 'directive' de OpenMP  
  
 Las cláusulas [copyprivate](../../parallel/openmp/reference/copyprivate.md) y [nowait](../../parallel/openmp/reference/nowait.md) son mutuamente excluyentes en la directiva especificada. Para corregir este error, quite una de las cláusulas `copyprivate` o `nowait` , o bien ambas.  
  
 El ejemplo siguiente genera la advertencia C3042:  
  
```  
// C3042.cpp  
// compile with: /openmp /c  
#include <stdio.h>  
#include "omp.h"  
  
double d;  
  
int main() {  
    #pragma omp parallel private(d)  
   {  
      #pragma omp single copyprivate(d) nowait   // C3042  
      {  
      }  
   }  
}  
```
