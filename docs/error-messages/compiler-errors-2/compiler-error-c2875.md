---
title: "Error del compilador C2875 | Microsoft Docs"
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
  - "C2875"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2875"
ms.assetid: d589fc0c-08b2-4a79-bc0e-dca5eb80bdd5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2875
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la declaración using crea una declaración múltiple de 'clase::identificador'  
  
 La declaración hace que se defina un mismo elemento dos veces.  
  
 El código siguiente genera el error C2875:  
  
```  
// C2875.cpp  
struct A {  
   void f(int*);  
};  
  
struct B {  
   void f(double*);  
};  
  
struct AB : A, B {  
   using A::f;  
   using A::f;   // C2875  
   using B::f;  
};  
```