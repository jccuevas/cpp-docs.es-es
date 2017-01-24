---
title: "Error del compilador C3612 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3612"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3612"
ms.assetid: aa6e3a2b-4afa-481c-98c1-1b6d1f82f869
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3612
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': una clase sealed no puede ser abstracta  
  
 Los tipos definidos con `value` \([\_\_value](../../misc/value.md)\) son sealed de forma predeterminada; asimismo, una clase es abstracta a menos que implemente todos los métodos de su base.  Una clase abstracta sealed no puede ser una clase base ni se pueden crear instancias de ella.  
  
 Para obtener más información, vea [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3612:  
  
```  
// C3612.cpp  
// compile with: /clr /c  
value struct V: public System::ICloneable {};   // C3612  
  
// OK  
value struct V2: public System::ICloneable {  
   Object^ Clone();  
};  
```