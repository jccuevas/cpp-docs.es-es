---
title: Compilador advertencia (nivel 3) C4280 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4280
dev_langs:
- C++
helpviewer_keywords:
- C4280
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6d4e9743a584249e2ec51c639423f56280f2d8f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4280"></a>Advertencia del compilador (nivel 3) C4280
'operador ->' era recursiva propio mediante el tipo 'type'  
  
 El código permite, incorrectamente **operador ->** llame a sí mismo.  
  
 El ejemplo siguiente genera C4280:  
  
```  
// C4280.cpp  
// compile with: /W3 /WX  
struct A  
{  
   int z;  
   A& operator ->();  
};  
  
void f(A y)  
{  
   int i = y->z; // C4280  
}  
```