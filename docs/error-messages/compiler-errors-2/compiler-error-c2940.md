---
title: "Error del compilador C2940 | Microsoft Docs"
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
  - "C2940"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2940"
ms.assetid: af6bf2bf-8de6-4cfd-bbf0-4c6b32a30edf
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2940
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': el id. de clase de tipo se ha redefinido como typedef local  
  
 No puede usar una clase genérica o de plantilla como `typedef` local.  
  
 El ejemplo siguiente genera la advertencia C2940:  
  
```  
// C2940.cpp template<class T> struct TC {}; int main() { typedef int TC<int>;   // C2940 typedef int TC;   // OK }  
```  
  
 También se puede producir C2940 al usar genéricos:  
  
```  
// C2940b.cpp // compile with: /clr generic<class T> ref struct GC { }; int main() { typedef int GC<int>;   // C2940 typedef int GC; }  
```