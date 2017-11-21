---
title: Error del compilador C3048 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3048
dev_langs: C++
helpviewer_keywords: C3048
ms.assetid: 48e07091-94d9-471d-befe-7e2507631edd
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a17a103bf49040496b886799bf58910eedff8051
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3048"></a>Error del compilador C3048
la forma de la expresión que va después de '#pragma omp atomic' no es adecuada  
  
 Una directiva atómica se especificó incorrectamente.  
  
 El ejemplo siguiente genera la advertencia C3048:  
  
```  
// C3048.cpp  
// compile with: /openmp vcomps.lib  
#include "omp.h"  
#include <stdio.h>  
  
int main() {  
   int a[10];  
   omp_set_num_threads(4);  
   #pragma omp parallel  
   {  
      #pragma omp atomic  
      a[0] = 1;   // C3048  
      // try the following line instead  
      // a[0] += 1;  
   }  
}  
```