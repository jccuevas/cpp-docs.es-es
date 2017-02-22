---
title: "Error del compilador C3160 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3160"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3160"
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3160
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'pointer': un miembro de datos de una clase administrada o WinRT no puede ser de este tipo  
  
 Los punteros interiores de recolección de elementos no utilizados pueden apuntar al interior de una clase administrada o WinRT.  Ya que son más lentos que los punteros de objetos completos y requieren un tratamiento especial por parte del recolector de elementos no utilizados, no puede declarar punteros interiores administrados como miembros de una clase.  
  
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
  
 **Extensiones administradas de C\+\+**  
  
 El ejemplo siguiente genera el error C3160:  
  
```  
// C3160b.cpp  
// compile with: /clr:oldSyntax  
  
__gc struct A {  
   // cannot create interior pointers inside a class  
   int __gc* pg; // C3160  
   int g;   // OK  
   int __nogc *pg2;   // OK  
};  
  
int main() {  
   int __gc* pg2;   // OK  
}  
```