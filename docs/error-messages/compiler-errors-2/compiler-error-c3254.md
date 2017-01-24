---
title: "Error del compilador C3254 | Microsoft Docs"
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
  - "C3254"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3254"
ms.assetid: 93427b10-fa72-4e43-80d1-1a6e122f9f40
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3254
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'reemplazo explícito' : la clase contiene el reemplazo explícito 'reemplazo', pero no deriva de una interfaz que contiene la declaración de función  
  
 Al [reemplazar explícitamente](../../cpp/explicit-overrides-cpp.md) un método, la clase que contiene el reemplazo debe derivarse, directa o indirectamente, del tipo que contiene la función que se reemplaza.  
  
 El código siguiente genera el error C3254:  
  
```  
// C3254.cpp  
__interface I  
{  
   void f();  
};  
  
__interface I1 : I  
{  
};  
  
struct A /* : I1 */  
{  
   void I1::f()  
   {   // C3254, uncomment : I1 to resolve this C3254  
   }  
};  
  
int main()  
{  
}  
```