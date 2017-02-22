---
title: "Error del compilador C2462 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2462"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2462"
ms.assetid: a8601bf8-f5ce-41de-9117-e2632bd4996b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2462
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : no se puede definir un tipo en una expresión 'new'  
  
 No se puede definir un tipo en el campo de operando del operador `new`.  Coloque la definición de tipo en una instrucción separada.  
  
 El código siguiente genera el error C2462:  
  
```  
// C2462.cpp  
int main() {  
   new struct S { int i; };   // C2462  
}  
```