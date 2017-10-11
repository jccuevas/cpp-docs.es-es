---
title: Error del compilador C3160 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3160
dev_langs:
- C++
helpviewer_keywords:
- C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: df09956b70d88b2ebb9efa542aad898f3d1295f2
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3160"></a>Error del compilador C3160
'pointer': un miembro de datos de una clase administrada o WinRT no puede ser de este tipo  
  
 Los punteros interiores de recolección de elementos no utilizados pueden apuntar al interior de una clase administrada o WinRT. Ya que son más lentos que los punteros de objetos completos y requieren un tratamiento especial por parte del recolector de elementos no utilizados, no puede declarar punteros interiores administrados como miembros de una clase.  
  
 El ejemplo siguiente genera el error C3160:  
  
```  
// C3160.cpp  
// compile with: /clr  
ref struct A {  
   // cannot create interior pointers inside a class  
   interior_ptr<int> pg;   // C3160  
   int g;   // OK  
   int* pg2;   // OK  
};  
  
int main() {  
   interior_ptr<int> pg2;   // OK  
}  
```  

