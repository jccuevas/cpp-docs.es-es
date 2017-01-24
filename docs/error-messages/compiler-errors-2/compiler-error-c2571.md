---
title: "Error del compilador C2571 | Microsoft Docs"
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
  - "C2571"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2571"
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2571
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : la función virtual no puede estar en la unión 'unión'  
  
 Se ha declarado una unión con una función virtual.  Una función virtual sólo se puede declarar en una clase o estructura.  Posible solución:  
  
1.  Cambie la unión por una clase o estructura.  
  
2.  Convierta la función en no virtual.  
  
 El código siguiente genera el error C2571:  
  
```  
// C2571.cpp  
// compile with: /c  
union A {  
   virtual void func1();   // C2571  
   void func2();   // OK  
};  
```