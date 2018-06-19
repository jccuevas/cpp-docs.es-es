---
title: Compilador advertencia (nivel 1) C4630 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4630
dev_langs:
- C++
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d3db4e42e4bd54e1d2bd5af0eb6b19ce0fea1e2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283317"
---
# <a name="compiler-warning-level-1-c4630"></a>Advertencia del compilador (nivel 1) C4630
'símbolo': especificador de clase de almacenamiento 'extern' no es válido para la definición de miembro  
  
 Un miembro de datos o una función miembro se define como `extern`. Miembros no pueden ser externos, aunque pueden de objetos completos. El compilador omite la `extern` palabra clave. El ejemplo siguiente genera C4630:  
  
```  
// C4630.cpp  
// compile with: /W1 /LD  
class A {  
   void func();  
};  
  
extern void A::func() {   // C4630, remove 'extern' to resolve  
}  
```