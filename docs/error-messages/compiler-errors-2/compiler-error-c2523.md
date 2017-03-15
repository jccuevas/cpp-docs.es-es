---
title: "Error del compilador C2523 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2523"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2523"
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2523
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase::~identifier' : etiqueta del destructor o finalizador sin correspondencia  
  
 El nombre del destructor debe ser el nombre de clase precedido por una tilde \(`~`\).  El constructor y el destructor son los únicos miembros que tienen el mismo nombre que la clase.  
  
 El código siguiente genera el error C2523:  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```