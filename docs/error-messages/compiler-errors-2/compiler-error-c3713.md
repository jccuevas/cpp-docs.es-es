---
title: "Error del compilador C3713 | Microsoft Docs"
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
  - "C3713"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3713"
ms.assetid: 75c6b9b6-955b-49bd-9bc8-ced88b496a1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3713
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'método': un método de control de eventos debe tener los mismos parámetros de función que el origen 'método'  
  
 Se definió un método de control de eventos que no devuelve los mismos parámetros que el método del evento de origen.  Para resolver este error, dé al método de control de eventos los mismos parámetros que los del método del evento de origen.  
  
 El código siguiente genera el error C3713:  
  
```  
// C3713.cpp  
// compile with: /c  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void event1(int nValue);  
   // try the following line instead  
   // __event void event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void handler1() {}  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3713  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3713  
   }  
};  
```