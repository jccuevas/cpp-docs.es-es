---
title: Compilador advertencia (nivel 1) C4804 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4804
dev_langs:
- C++
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 677899230b2475c80f9bdd461a0c79740c4d3bec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4804"></a>Advertencia del compilador (nivel 1) C4804
'operación': uso no seguro del tipo 'bool' en la operación  
  
 Esta advertencia es adecuada cuando usa un `bool` variable o un valor de forma inesperada. Por ejemplo, se genera C4804 si se usan operadores como el operador unario negativo (**-**) o el operador de complemento (`~`). El compilador evalúa la expresión.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4804:  
  
```  
// C4804.cpp  
// compile with: /W1  
  
int main()  
{  
   bool i = true;  
   if (-i)   // C4804, remove the '-' to resolve  
   {  
      i = false;  
   }  
}  
```