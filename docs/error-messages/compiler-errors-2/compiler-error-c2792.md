---
title: "Error del compilador C2792 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2792"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2792"
ms.assetid: 392cf748-4f5e-4e62-a364-3118d5658408
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2792
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'super': esta palabra clave debe ir seguida de '::'  
  
 El único símbolo \(token\) que puede ir a continuación de la palabra clave `__super` es `::`.  
  
 El código siguiente genera el error C2792:  
  
```  
// C2792.cpp  
struct B {  
   void mf();  
};  
  
struct D : B {  
   void mf() {  
      __super.();   // C2792  
  
      // try the following line instead  
      // __super::mf();  
   }  
};  
```