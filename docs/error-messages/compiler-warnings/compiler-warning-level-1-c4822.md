---
title: "Advertencia del compilador (nivel 1) C4822 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4822"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4822"
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4822
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member': la función miembro de clase local no tiene cuerpo  
  
 Una función de miembro de clase local se ha declarado, pero no se ha definido en la clase. Para usar una función de miembro de clase local, debe definirla en la clase. No se puede declarar en la clase y definirla fuera de ella.  
  
 Cualquier definición de la clase de una función miembro de clase local será un error.  
  
 El ejemplo siguiente genera la advertencia C4822:  
  
```  
// C4822.cpp // compile with: /W1 int main() { struct C { void func1(int);   // C4822 // try the following line instead // void func1(int){} }; }  
```