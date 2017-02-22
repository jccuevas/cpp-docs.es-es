---
title: "Error del compilador C2180 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2180"
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2180
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la expresión de control es del tipo 'type'  
  
 La expresión de control es `if`, `while` o `for`, o la instrucción `do` es una expresión convertida en `void`.  Para corregir este problema, cambie la expresión de control por otra que produzca `bool` o un tipo que se pueda convertir en `bool`.  
  
 El ejemplo siguiente genera el error C2180:  
  
```  
// C2180.c  
  
int main() {  
   while ((void)1)   // C2180  
      return 1;  
   while (1)         // OK  
      return 0;  
}  
```