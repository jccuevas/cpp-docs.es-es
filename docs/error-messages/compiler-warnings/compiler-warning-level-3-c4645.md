---
title: Compilador advertencia (nivel 3) C4645 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4645
dev_langs:
- C++
helpviewer_keywords:
- C4645
ms.assetid: fd7c1ddf-f0d0-4e10-bab9-ccb4c3476298
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 718afb6b8336e36e0c0244cbdccd8af16ac4167f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4645"></a>Advertencia del compilador (nivel 3) C4645
la función declarada con __declspec(noreturn) tiene una instrucción return  
  
 A [return](../../cpp/return-statement-in-program-termination-cpp.md) en una función marcada con el modificador [noreturn](../../cpp/noreturn.md) `__declspec` . Se omitió la instrucción `return` .  
  
 El ejemplo siguiente genera la advertencia C4645:  
  
```  
// C4645.cpp  
// compile with:  /W3  
void __declspec(noreturn) func() {  
   return;   // C4645, delete this line to resolve  
}  
  
int main() {  
}  
```