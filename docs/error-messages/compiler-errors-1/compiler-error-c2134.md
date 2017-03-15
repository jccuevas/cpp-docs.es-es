---
title: C2134 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2134
dev_langs:
- C++
ms.assetid: d45cb3e8-0be4-4bd6-8be9-5f8d2384363f
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 5d249fd24f575ef99b537b1993761bcf168ca803
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2134"></a>C2134 de Error del compilador
'función': llamada no se produce en una expresión constante  
  
 Declara una función declarada como constexpr sólo puede llamar a otras funciones como constexpr.  
  
 El ejemplo siguiente genera C2134:  
  
```  
// C2134.cpp  
// compile with: /c  
int A() {  
    return 42;  
};  
  
constexpr int B() {  
    return A();  // Error C2134: 'A': call does not result in a constant expression.  
}  
```  
  
 Posible solución:  
  
```  
// C2134b.cpp  
constexpr int A() {  // add constexpr to A, since it meets the requirements of constexpr.  
    return 42;  
};  
  
constexpr int B() {  
    return A();  // No error  
}  
```
