---
title: "Advertencia del compilador (nivel 4) C4913 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4913"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4913"
ms.assetid: b94aa52e-6029-4170-9134-017714931546
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4913
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**el operador binario ',' definido por el usuario existe pero ninguna sobrecarga puede convertir todos los operandos; en su lugar, se utilizará el operador binario ',' incorporado**  
  
 Se produjo una llamada al operador coma integrado en un programa que también tenía un operador coma sobrecargado; no se ejecutó una conversión que creía que se había producido.  
  
 El ejemplo siguiente genera la advertencia C4913:  
  
```  
// C4913.cpp // compile with: /W4 struct A { }; struct S { }; struct B { // B() { } // B(S &s) { s; } }; B operator , (A a, B b) { a; return b; } int main() { A a; B b; S s; a, b;   // OK calls user defined operator a, s;   // C4913 uses builtin comma operator // uncomment the conversion code in B to resolve. }  
```