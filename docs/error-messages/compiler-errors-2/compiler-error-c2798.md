---
title: "Error del compilador C2798 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2798"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2798"
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2798
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'super::miembro' es ambiguo  
  
 Hay varias estructuras heredadas que contienen el miembro al que se ha hecho referencia con [super](../../cpp/super.md).  Se puede resolver el error:  
  
-   Quitando B1 o B2 de la lista de herencia de D.  
  
-   Cambiando el nombre del miembro de datos en B1 o B2.  
  
 El código siguiente genera el error C2798:  
  
```  
// C2798.cpp  
struct B1 {  
   int i;  
};  
  
struct B2 {  
   int i;  
};  
  
struct D : B1, B2 {  
   void g() {  
      __super::i = 4; // C2798  
   }  
};  
```