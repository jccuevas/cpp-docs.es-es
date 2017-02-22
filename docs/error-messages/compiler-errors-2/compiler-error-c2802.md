---
title: "Error del compilador C2802 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2802"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2802"
ms.assetid: 08b68c0e-9382-40ac-8949-39a7a2749e05
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2802
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el miembro estático 'operator operador' no tiene parámetros formales  
  
 Un operador declarado por una función miembro `static` debe tener al menos un parámetro.  
  
 El código siguiente genera el error C2802:  
  
```  
// C2802.cpp  
// compile with: /clr /c  
ref class A {  
   static operator+ ();   // C2802  
   static operator+ (A^, A^);   // OK  
};  
```