---
title: "Error del compilador C3240 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3240"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3240"
ms.assetid: 1a8dc213-b80c-47ae-ada0-e9554b635d1e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3240
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : debe ser una función miembro abstracta no sobrecargada de 'tipo'  
  
 Un tipo base contenía una función que se había definido.  La función debe ser virtual.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3240.  
  
```  
// C3240.cpp  
// compile with: /c  
__interface I {  
   void f();  
};  
  
struct A1 : I {   
   void f() {}  
};  
  
struct A2 : I {   
   void f() = 0;  
};  
  
template <class T>   
struct A3 : T {  
   void T::f() {}  
};  
  
template <class T>   
struct A4 : T {  
   void T::f() {}  
};  
  
A3<A1> x;   // C3240  
A3<I> x2;  
A4<A2> x3;  
```