---
title: Error del compilador C3007 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3007
dev_langs: C++
helpviewer_keywords: C3007
ms.assetid: e415ef42-bdc9-4f32-8198-5e25b289a089
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4c8bb7b96f1ef86b4b667c0f8566d893e695f1cc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3007"></a>Error del compilador C3007
'arg': la cláusula de la directiva 'directiva' de OpenMP no toma un argumento.  
  
 Una directiva de OpenMP tenía un argumento, pero la directiva no toma un argumento.  
  
 El ejemplo siguiente genera la advertencia C3007:  
  
```  
// C3007.c  
// compile with: /openmp  
int main()  
{  
   #pragma omp parallel for ordered(2)   // C3007  
}  
```