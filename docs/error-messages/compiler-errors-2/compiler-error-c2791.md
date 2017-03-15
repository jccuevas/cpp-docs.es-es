---
title: "Error del compilador C2791 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2791"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2791"
ms.assetid: 938ad1fb-75d9-4ce2-ad92-83d6249005b5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2791
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

uso no válido de 'super': 'clase' no tiene clases base  
  
 Se utilizó la palabra clave [super](../../cpp/super.md) en el contexto de una función miembro de una clase que no posee clases base.  
  
 El código siguiente genera el error C2791:  
  
```  
// C2791.cpp  
struct D {  
   void mf() {  
      __super::mf();   // C2791  
   }  
};  
```