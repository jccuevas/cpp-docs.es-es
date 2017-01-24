---
title: "Error del compilador C3711 | Microsoft Docs"
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
  - "C3711"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3711"
ms.assetid: 26d581cc-2153-4ee0-b814-a371184be3e1
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3711
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'método': un método de origen de eventos no administrado debe devolver void o un tipo entero  
  
 Se ha definido un método en el origen de eventos que no devuelve void ni un tipo entero.  Para resolver este error, haga que tanto el evento como su controlador tengan un tipo de valor devuelto `void` o un tipo entero como `int` o `long`.  
  
 El código siguiente genera el error C3711:  
  
```  
// C3711.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[event_source(native)]  
class CEventSrc {  
public:  
   __event float event1();   // C3711  
   // try the following line instead  
   // __event int event1();  
   // also change the handler, below  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   float handler1() {         // change float to int  
      return 0.0;             // change 0.0 to 0  
   }  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(CEventSrc::event1, pSrc, CEventRec::handler1);  
   }  
};  
  
int main() {  
}  
```