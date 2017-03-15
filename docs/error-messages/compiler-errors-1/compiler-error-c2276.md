---
title: "Error del compilador C2276 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2276"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2276"
ms.assetid: 62005ad9-6cb9-4b1f-965d-b875adaf695e
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2276
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador': operación no válida de la expresión de función miembro enlazada  
  
 El compilador ha encontrado un problema en la sintaxis para crear un puntero a miembro.  
  
 El código siguiente genera el error C2276:  
  
```  
// C2276.cpp  
class A {  
public:  
   int func(){return 0;}  
} a;  
  
int (*pf)() = &a.func;   // C2276  
// try the following line instead  
// int (A::*pf3)() = &A::func;  
  
class B {  
public:  
   void mf() {  
      &this -> mf;   // C2276  
      // try the following line instead  
      // &B::mf;  
   }  
};  
  
int main() {  
   A a;  
   &a.func;   // C2276  
   // try the following line instead  
   // &A::func;  
}  
```