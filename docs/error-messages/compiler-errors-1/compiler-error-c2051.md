---
title: "Error del compilador C2051 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2051"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2051"
ms.assetid: 81c0469a-78e2-49fa-bd76-97cdb135e3ea
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2051
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la expresión case no es una constante  
  
 Las expresiones case deben ser constantes de tipo entero.  
  
 El código siguiente genera el error C2051:  
  
```  
// C2051.cpp  
class X {};  
  
int main() {  
   static X x;  
   int i = 0;  
  
   switch (i) {  
      case x:   // C2051 use constant expression to resolve error  
         break;  
      default:  
         break;  
   }  
}  
```  
  
 Posible solución:  
  
```  
// C2051b.cpp  
class X {};  
  
int main() {  
   static X x;  
   int i = 0;  
  
   switch (i) {  
      case 1:  
         break;  
      default:  
         break;  
   }  
}  
```