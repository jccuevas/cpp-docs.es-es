---
title: Compilador advertencia (nivel 1) C4537 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4537
dev_langs:
- C++
helpviewer_keywords:
- C4537
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c3762d79d5c6937eb23428fe00b86b1489ea869a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286060"
---
# <a name="compiler-warning-level-1-c4537"></a>Advertencia del compilador (nivel 1) C4537
'object': 'operador' aplicado al tipo no definido por el usuario  
  
 Se pasó una referencia cuando se esperaba un objeto (tipo definido por el usuario). Una referencia no es un objeto, pero no es capaz de hacer una distinción código ensamblador alineado. El compilador genera código como si fuesen ***objeto*** fuera una instancia.  
  
 El ejemplo siguiente genera C4537:  
  
```  
// C4537.cpp  
// compile with: /W1 /c  
// processor: x86  
struct S {  
   int member;  
};  
  
void f1(S &s) {  
   __asm mov eax, s.member;   // C4537  
   // try the following code instead  
   // or, make the declaration "void f1(S s)"  
   /*  
   mov eax, s  
   mov eax, [eax]s.member  
   */  
}  
```