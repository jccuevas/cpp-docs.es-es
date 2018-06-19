---
title: Error del compilador C3055 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3055
dev_langs:
- C++
helpviewer_keywords:
- C3055
ms.assetid: 60446ee0-18dd-48fc-9059-f0a14229dce8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 309ebcbd2b13baa78e0ef814be244a1c1ddaee33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33249851"
---
# <a name="compiler-error-c3055"></a>Error del compilador C3055
'símbolo': no se puede hacer referencia al símbolo antes de que se use en la directiva 'threadprivate'  
  
 Se hizo referencia a un símbolo y luego se lo usó en una cláusula [threadprivate](../../parallel/openmp/reference/threadprivate.md) , pero esto no se permite.  
  
 El ejemplo siguiente genera la advertencia C3055:  
  
```  
// C3055.cpp  
// compile with: /openmp  
int x, y;  
int z = x;  
#pragma omp threadprivate(x, y)   // C3055  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```  
  
 Posible resolución:  
  
```  
// C3055b.cpp  
// compile with: /openmp /LD  
int x, y, z;  
#pragma omp threadprivate(x, y)  
  
void test() {  
   #pragma omp parallel copyin(x, y)  
   {  
      x = y;  
   }  
}  
```