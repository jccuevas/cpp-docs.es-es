---
title: Compilador advertencia (nivel 1) C4550 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4550
dev_langs:
- C++
helpviewer_keywords:
- C4550
ms.assetid: f902b4ed-5f17-48ea-b693-92f4fb8c8054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d08529006e54427e4327ce96666e551046c07e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4550"></a>Advertencia del compilador (nivel 1) C4550
expresión se evalúa como una función que le falta una lista de argumentos  
  
 Un puntero sin referencia a una función le falta una lista de argumentos.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4550.cpp  
// compile with: /W1  
bool f()  
{  
   return true;  
}  
  
typedef bool (*pf_t)();  
  
int main()  
{  
   pf_t pf = f;  
   if (*pf) {}  // C4550  
   return 0;  
}  
```