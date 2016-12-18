---
title: "Error del compilador C3207 | Microsoft Docs"
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
  - "C3207"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3207"
ms.assetid: 4a28b976-142a-4cff-aa2f-480b892c50ca
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3207
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': argumento de plantilla de 'arg' no válido, se esperaba una plantilla de clase  
  
 Se definió una función de plantilla como si tomara un argumento de tipo de plantilla. Sin embargo, se pasó un argumento de tipo de plantilla.  
  
 El ejemplo siguiente genera la advertencia C3207:  
  
```  
// C3207.cpp template <template <class T> class TT> void f(){} template <class T> struct S { }; void f1() { f<S<int> >();   // C3207 // try the following line instead // f<S>(); }  
```