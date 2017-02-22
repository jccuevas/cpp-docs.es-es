---
title: "Error del compilador C2032 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2032"
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': la función no puede ser miembro de struct\/union 'estructuraounión'  
  
 La estructura o unión tiene una función miembro, permitida en C\+\+ pero no en C.  Para solucionar el problema, compile como programa de C\+\+ o quite la función miembro.  
  
 El código siguiente genera el error C2032:  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 Posible solución:  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```