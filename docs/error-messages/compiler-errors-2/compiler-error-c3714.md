---
title: "Error del compilador C3714 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3714"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3714"
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3714
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'método': un método de control de eventos debe tener la misma convención de llamada que el origen 'método'  
  
 Se definió un método de control de eventos que no utiliza la misma convención de llamada que el método del evento de origen.  Para resolver este error, dé al método de control de eventos la misma convención de llamada que la del método del evento de origen.  Por ejemplo, en el código de ejemplo siguiente, haga coincidir las convenciones de llamada de `handler1` y `event1` \([\_\_cdecl](../../cpp/cdecl.md) o [\_\_stdcall](../../cpp/stdcall.md) u otras\).  Quitar las palabras clave de convención de llamada de ambas declaraciones también resolverá el problema, haciendo que `event1` y `handler1` utilicen de forma predeterminada la convención de llamada [thiscall](../../cpp/thiscall.md).  Vea [Convenciones de llamada](../../cpp/calling-conventions.md) para obtener más información.  
  
 El código siguiente genera el error C3714:  
  
```  
// C3714.cpp  
// compile with: /c  
// processor: x86  
[event_source(native)]  
class CEventSrc {  
public:  
   __event void __cdecl event1();  
   // try the following line instead  
   // __event void __stdcall event1();  
};  
  
[event_receiver(native)]  
class CEventRec {  
public:  
   void __stdcall handler1() {}  
  
   void HookEvents(CEventSrc* pSrc) {  
      __hook(&CEventSrc::event1, pSrc, &CEventRec::handler1);   // C3714  
   }  
  
   void UnhookEvents(CEventSrc* pSrc) {  
      __unhook(&CEventSrc::event1, pSrc, &CEventRec::handler1); // C3714  
   }  
};  
```