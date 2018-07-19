---
title: Error del compilador C3034 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3034
dev_langs:
- C++
helpviewer_keywords:
- C3034
ms.assetid: 49db8bac-2720-4622-94e3-7988f1603fa3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41918704bb00df2950079c80d2615e63fdfb4525
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247020"
---
# <a name="compiler-error-c3034"></a>Error del compilador C3034
La directiva 'directive1' de OpenMP no se puede anidarse directamente dentro de la directiva 'directive2'  
  
 Algunas directivas no se pueden anidar. Para corregir este error, puede combinar las instrucciones de ambas directivas en el bloque de una directiva, o bien construir directivas consecutivas.  
  
 El ejemplo siguiente genera la advertencia C3034:  
  
```  
// C3034.cpp  
// compile with: /openmp /link vcomps.lib  
int main() {  
  
   #pragma omp single  
   {  
      #pragma omp single   // C3034   
      {  
      ;  
      }  
   }  
  
   // Two consecutive single clauses are OK.  
   #pragma omp single  
   {  
   }  
  
   #pragma omp single  
   {  
   }  
}  
```