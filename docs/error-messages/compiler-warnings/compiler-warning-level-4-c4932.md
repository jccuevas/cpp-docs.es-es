---
title: "Advertencia del compilador (nivel 4) C4932 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4932"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4932"
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Advertencia del compilador (nivel 4) C4932
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_identifier\(identifier\) e \_\_identifier\(identifier\) no se pueden distinguir  
  
 El compilador es no puede distinguir entre **\_finally** y `__finally` o entre `__try` y **\_try** como parámetro pasado a [\_\_identifier](../../windows/identifier-cpp-cli.md). No debería intentar usar ambos como identificadores en el mismo programa, ya que provocarán un error [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md).  
  
 El ejemplo siguiente genera la advertencia C4932:  
  
```  
// C4932.cpp // compile with: /clr /W4 /WX int main() { int __identifier(_finally) = 245;   // C4932 int __identifier(__finally) = 25;   // C4932 }  
```