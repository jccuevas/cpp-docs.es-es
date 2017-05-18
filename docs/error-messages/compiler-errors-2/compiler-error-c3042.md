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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: d6e26077e9ced646615681c1472661145939887a
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3042"></a>Error del compilador C3042
Las cláusulas 'copyprivate' y 'nowait' no pueden aparecer juntas en la directiva 'directive' de OpenMP  
  
 El [copyprivate](../../parallel/openmp/reference/copyprivate.md) y [nowait](../../parallel/openmp/reference/nowait.md) cláusulas son mutuamente excluyentes en la directiva especificada. Para corregir este error, quite una de las cláusulas `copyprivate` o `nowait` , o bien ambas.  
  
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
