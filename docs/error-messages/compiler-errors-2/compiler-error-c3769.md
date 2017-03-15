---
title: "Error del compilador C3769 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3769"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3769"
ms.assetid: 341675e1-7428-4da6-8275-1b2f0a70dacc
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3769
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : una clase anidada no puede tener el mismo nombre que la clase inmediatamente envolvente  
  
 Una clase anidada no puede tener el mismo nombre que la clase envolvente inmediata.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3769.  
  
```  
// C3769.cpp  
// compile with: /c  
class x {  
   class x {};   // C3769  
   class y {  
      class x{};   // OK  
   };  
};  
```