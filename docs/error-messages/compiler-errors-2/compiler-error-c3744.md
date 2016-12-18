---
title: "Error del compilador C3744 | Microsoft Docs"
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
  - "C3744"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3744"
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3744
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_unhook debe tener al menos 3 argumentos para eventos administrados  
  
 La función [\_\_unhook](../../cpp/unhook.md) debe tomar tres parámetros al usarla en un programa compilado para Extensiones administradas para C\+\+.  
  
 `__hook` y `__unhook` no son compatibles con la programación \/clr.  Utilice los operadores \+ \= y \- \= en su lugar.  
  
 Sólo se puede reproducir el error C3744 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3744:  
  
```  
// C3744.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
public __delegate void delegate1();  
  
[ event_source(managed) ]  
public __gc class CPSource {  
public:  
   __event delegate1* event1;  
};  
  
[event_receiver(managed)]  
public __gc class CReceiver {  
public:  
   void Handler1() {  
   }  
  
   void UnhookAll1(CPSource* pSrc, CReceiver* pRec) {  
      pRec;  
      __unhook(pSrc);   // C3744  
      // The following line resolves the error.  
      // __unhook(&CPSource::event1, pSrc, &CReceiver::Handler1);  
   }  
};  
  
int main() {  
}  
```