---
title: "Error del compilador C2594 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2594"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2594"
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# Error del compilador C2594
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : conversiones ambiguas de 'tipo1' a 'tipo2'  
  
 Ninguna conversión de *type1* a *type2* más directa que cualquier otro.  Sugerimos dos posibles soluciones para convertir de *type1* a *type2*.  La primera opción consiste en definir una conversión directa de *type1* a *type2*, y la segunda consiste en especificar una secuencia de conversiones de *type1* a *type2*.  
  
 El ejemplo siguiente genera el error C2594.  La solución sugerida para el error es una secuencia de conversiones:  
  
```  
// C2594.cpp  
// compile with: /c  
struct A{};  
struct I1 : A {};  
struct I2 : A {};  
struct D : I1, I2 {};  
  
A *f (D *p) {  
   return (A*) (p);    // C2594  
  
// try the following line instead  
// return static_cast<A *>(static_cast<I1 *>(p));  
}  
```