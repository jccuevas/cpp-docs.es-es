---
title: "Error del compilador C3066 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3066"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3066"
ms.assetid: 226f6de5-c4c5-41e2-b31a-2e30a37fbbeb
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3066
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

hay varias formas mediante las que se puede llamar a un objeto de este tipo con estos argumentos  
  
 El compilador ha detectado una llamada a una función ambigua que requiere suplentes.  
  
 El código siguiente genera el error C3066:  
  
```  
// C3066.cpp  
template <class T, class U> void func(T*, U*){}  
  
typedef void (*PF)(const int*, const char*);  
typedef void (*PF1)(const int*, volatile char*);  
  
struct A {  
   operator PF() const {  
      return func;  
   }  
  
   operator PF1() {  
      return func;  
   }  
  
   operator PF1() const  {  
      return func;  
   }  
  
};  
  
int main() {  
   A a;  
   int i;  
   char c;  
  
   a(&i, &c);   // C3066  
   a(&i, (const char *) &c);   // OK  
}  
```