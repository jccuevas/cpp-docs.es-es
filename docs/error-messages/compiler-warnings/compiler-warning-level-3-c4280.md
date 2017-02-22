---
title: "Advertencia del compilador (nivel 3) C4280 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4280"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4280"
ms.assetid: 153fb639-3ee1-4fee-baf9-71420abcf3f6
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 3) C4280
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador –\>' era auto\-recursivo mediante el tipo “tipo”  
  
 El código permite incorrectamente que **operator–\>** se denomina.  
  
 El código siguiente genera el error C4280:  
  
```  
// C4280.cpp  
// compile with: /W3 /WX  
struct A  
{  
   int z;  
   A& operator ->();  
};  
  
void f(A y)  
{  
   int i = y->z; // C4280  
}  
```