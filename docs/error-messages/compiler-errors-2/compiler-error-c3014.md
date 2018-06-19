---
title: Error del compilador C3014 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3014
dev_langs:
- C++
helpviewer_keywords:
- C3014
ms.assetid: af1c5b0c-dbf9-4274-b06a-c6c2cdcf2a52
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5623d64adc3fc5f47e4dd63a82078906a11db1b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33243152"
---
# <a name="compiler-error-c3014"></a>Error del compilador C3014
se esperaba un bucle for después de la directiva 'directive' de OpenMP  
  
 Es un error para cualquier cosa que no sea un bucle `for` seguir inmediatamente a una directiva `#pragma omp for` .  
  
 El ejemplo siguiente genera la advertencia C3014:  
  
```  
// C3014.cpp  
// compile with: /openmp  
int main()  
{  
   int i = 0;  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      for (i = 0; i < 10; ++i)   // OK  
      {  
      }  
   }  
  
   #pragma omp parallel for  
   for (i = 0; i < 10; ++i)   // OK  
   {  
   }  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      {   // C3014  
         for (i = 0; i < 10; ++i)  
         {  
         }  
      }  
   }  
  
   #pragma omp parallel for  
   {   // C3014  
      for (i = 0; i < 10; ++i)  
      {  
      }  
   }  
  
   #pragma omp parallel  
   {  
      #pragma omp for  
      i *= 2;   // C3014  
      for (i = 0; i < 10; ++i)  
      {  
      }  
   }  
  
   #pragma omp parallel for  
   i *= 2;   // C3014  
   for (i = 0; i < 10; ++i)  
   {  
   }  
}  
```