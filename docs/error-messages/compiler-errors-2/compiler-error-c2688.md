---
title: "Error del compilador C2688 | Microsoft Docs"
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
  - "C2688"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2688"
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2688
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'C2::fgrv': los resultados de covariante con herencia múltiple o virtual no son compatibles con funciones varargs  
  
 Los tipos de valor devuelto de covariante no se admiten en Visual C\+\+ cuando una función contiene argumentos de variable.  
  
 Para resolver este error, defina las funciones para que no utilicen argumentos de variable o bien haga que los valores devueltos sean los mismos para todas las funciones virtuales.  
  
 El código siguiente genera el error C2688:  
  
```  
// C2688.cpp  
struct G1 {};  
struct G2 {};  
struct G3 : G1, G2 {};  
struct G4 {};  
struct G5 {};  
struct G6 : G4, G5 {};  
struct G7 : G3, G6 {};  
  
struct C1 {  
   virtual G4& fgrv(int,...);  
};  
  
struct C2 : C1 {  
   virtual G7& fgrv(int,...);   // C2688, does not return G4&  
};  
```