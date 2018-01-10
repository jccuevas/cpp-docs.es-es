---
title: Error del compilador C3013 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3013
dev_langs: C++
helpviewer_keywords: C3013
ms.assetid: f896777d-27e6-4b6d-baab-1567317f3374
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 843f3d8e74574a473c1c29826b3e753277e6aacc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3013"></a>Error del compilador C3013
'clause': la cláusula solamente puede aparecer una vez en la directiva 'directive' de OpenMP  
  
 Una cláusula apareció dos veces en la misma directiva. Elimine una aparición de la cláusula.  
  
 El ejemplo siguiente genera la advertencia C3013:  
  
```  
// C3013.cpp  
// compile with: /openmp  
int main() {  
   int a, b, c, x, y, z;  
  
   #pragma omp parallel shared(a,b,c) private(x)  
  
   #pragma omp for nowait private(x) nowait   // C3013  
   // The previous line generates C3013, with two nowait clauses  
   // try the following line instead:  
   // #pragma omp for nowait private(x)  
   for (a = 0 ; a < 10 ; ++a) {  
   }  
}  
```