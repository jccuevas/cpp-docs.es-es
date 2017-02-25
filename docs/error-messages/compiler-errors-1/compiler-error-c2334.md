---
title: "Error del compilador C2334 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2334"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2334"
ms.assetid: 36142855-e00b-4bbf-80f5-a301edeff46e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2334
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

símbolos \(token\) inesperados delante de ': or {'; se pasará por alto el cuerpo de función aparente  
  
 El ejemplo siguiente genera el error C2334.  Este error se produce después del error C2059:  
  
```  
// C2334.cpp  
// compile with: /c  
// C2059 expected  
struct s1 {  
   s1   {}   // C2334  
   s1() {}   // OK  
};  
```