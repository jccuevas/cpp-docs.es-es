---
title: "Error del compilador C2157 | Microsoft Docs"
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
  - "C2157"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2157"
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2157
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function': se debe declarar antes de usarse en la lista pragma  
  
 El nombre de función no se declara antes de que se le haga referencia en la lista de funciones de una pragma [alloc\_text](../../preprocessor/alloc-text.md).  
  
 El ejemplo siguiente genera la advertencia C2157:  
  
```  
// C2157.cpp // compile with: /c #pragma alloc_text( "func", func)   // C2157 // OK extern "C" void func(); #pragma alloc_text( "func", func)  
```