---
title: "Error del compilador C2344 | Microsoft Docs"
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
  - "C2344"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2344"
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2344
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

align\(\#\): la alineación debe ser potencia de dos  
  
 Cuando se usa la palabra clave [align](../../cpp/align-cpp.md), el valor pasado debe ser una potencia de dos.  
  
 Por ejemplo, el código siguiente genera el error C2344 porque 3 no es una potencia de dos:  
  
```  
// C2344.cpp // compile with: /c __declspec(align(3)) int a;   // C2344 __declspec(align(4)) int b;   // OK  
```