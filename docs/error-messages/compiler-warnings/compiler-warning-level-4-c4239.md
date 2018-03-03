---
title: Compilador advertencia (nivel 4) C4239 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4239
dev_langs:
- C++
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 18f1c6d700de0c621ebde02c7dcb2817091677cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4239"></a>Advertencia del compilador (nivel 4) C4239
ha utilizado una extensión no estándar: 'token': conversión de 'tipo' a 'tipo'  
  
 Esta conversión de tipo no está permitida por el estándar de C++, pero se permite aquí como una extensión. Esta advertencia siempre va seguida de al menos una línea de explicación que describe la regla de idioma que se ha infringido.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4239.  
  
```  
// C4239.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
void func(void) {  
   C & rC = C();   // C4239  
   const C & rC2 = C();   // OK  
   rC2;  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Conversión de tipo entero a un tipo enum no se permite estrictamente.  
  
 El ejemplo siguiente genera C4239.  
  
```  
// C4239b.cpp  
// compile with: /W4 /c  
enum E { value };   
struct S {   
   E e : 2;   
} s = { 5 };   // C4239   
// try the following line instead  
// } s = { (E)5 };  
```