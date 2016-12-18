---
title: "Advertencia del compilador (nivel 1) C4537 | Microsoft Docs"
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
  - "C4537"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4537"
ms.assetid: 9454493c-d419-475e-8f35-9c00233c9329
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4537
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'objeto' : 'operador' aplicado a un tipo que no es un tipo definido por el usuario  
  
 Se pasó una referencia pero se esperaba un objeto \(tipo definido por el usuario\).  Una referencia no es un objeto, pero el código ensamblador en línea no puede detectar la diferencia.  El compilador genera código como si ***object*** fuera una instancia.  
  
 El código siguiente genera el error C4537:  
  
```  
// C4537.cpp  
// compile with: /W1 /c  
// processor: x86  
struct S {  
   int member;  
};  
  
void f1(S &s) {  
   __asm mov eax, s.member;   // C4537  
   // try the following code instead  
   // or, make the declaration "void f1(S s)"  
   /*  
   mov eax, s  
   mov eax, [eax]s.member  
   */  
}  
```