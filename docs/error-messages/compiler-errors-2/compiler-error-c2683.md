---
title: C2683 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2683
dev_langs:
- C++
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 35619d93200c2f0e61dbf903f56a70bbe0c48d73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2683"></a>C2683 de Error del compilador
'cast': 'tipo' no es un tipo polimórfico  
  
 No se puede utilizar [dynamic_cast](../../cpp/dynamic-cast-operator.md) para convertir desde una clase no polimórfica (una clase sin funciones virtuales).  
  
 Puede usar [static_cast](../../cpp/static-cast-operator.md) para realizar conversiones de tipos no polimórficos. Sin embargo, `static_cast` no lleva a cabo una comprobación en tiempo de ejecución.  
  
 El ejemplo siguiente genera C2683:  
  
```  
// C2683.cpp  
// compile with: /c  
class B { };  
class D : public B { };  
  
void f(B* pb) {  
   D* pd1 = dynamic_cast<D*>(pb);  // C2683  
   D* pd1 = static_cast<D*>(pb);   // OK  
}  
```