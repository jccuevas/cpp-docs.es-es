---
title: Error del compilador C3714 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3714
dev_langs: C++
helpviewer_keywords: C3714
ms.assetid: 17718f75-5a37-4e42-912b-487e91008a95
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 69f3f5c90524b02cad8a36babaceeb32544e7aff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3714"></a>Error del compilador C3714
'método': un método de controlador de eventos debe tener la misma convención de llamada que el origen 'método'  
  
 Define un método de controlador de eventos que no utiliza la misma convención de llamada que el método de evento de origen. Para corregir este error, dé al método de controlador de eventos las mismas convenciones de llamada que los del método del evento de origen. Por ejemplo, en el código siguiente, realice las convenciones de llamada de `handler1` y `event1` coincidir con ([__cdecl](../../cpp/cdecl.md) o [__stdcall](../../cpp/stdcall.md) u otros). Quitar palabras clave de convención de llamada de ambas declaraciones también resuelve el problema y provocar `event1` y `handler1` en de forma predeterminada el [thiscall](../../cpp/thiscall.md) convención de llamada. Vea [convenciones de llamada](../../cpp/calling-conventions.md) para obtener más información.  
  
 El ejemplo siguiente genera C3714:  
  
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