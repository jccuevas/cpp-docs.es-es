---
title: Compilador advertencia (nivel 3) C4243 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4243
dev_langs:
- C++
helpviewer_keywords:
- C4243
ms.assetid: ca72f9ad-ce0b-43a9-a68c-106e1f8b90ef
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ab21da8a86eab959e80699f66acd3befffb70707
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-3-c4243"></a>Advertencia del compilador (nivel 3) C4243
' tipo de conversión ' existe desde 'tipo1' a 'tipo2', pero no es accesible  
  
 Un puntero a una clase derivada se convierte en un puntero a una clase base, pero la clase derivada hereda de la clase base con acceso privado o protegido.  
  
 El ejemplo siguiente genera C4243:  
  
```  
// C4243.cpp  
// compile with: /W3  
// C4243 expected  
struct B {  
   int f() {  
      return 0;  
   };  
};  
  
struct D : private B {};  
struct E : public B {};  
  
int main() {  
   // Delete the following 2 lines to resolve.  
   int (D::* d)() = (int(D::*)()) &B::f;   
   d;  
  
   int (E::* e)() = (int(E::*)()) &B::f; // OK  
   e;  
}  
```
