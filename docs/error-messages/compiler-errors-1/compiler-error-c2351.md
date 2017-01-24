---
title: "Error del compilador C2351 | Microsoft Docs"
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
  - "C2351"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2351"
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2351
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sintaxis de inicialización del constructor de C\+\+ obsoleta  
  
 En una lista de inicialización de nuevo estilo para un constructor, se deben denominar explícitamente cada una de las clase base directas, aun cuando sólo haya una clase base.  
  
 El código siguiente genera el error C2351:  
  
```  
// C2351.cpp  
// compile with: /c  
class B {  
public:   
   B() : () {}   // C2351  
   B() {}   // OK  
};  
```