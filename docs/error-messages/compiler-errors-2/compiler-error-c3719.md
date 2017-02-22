---
title: "Error del compilador C3719 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3719"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3719"
ms.assetid: d0d59d4e-babb-4480-9ef7-70cf1a28165c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3719
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'interfaz': un origen de eventos basado en una interfaz sólo se puede utilizar para eventos COM  
  
 Se ha declarado un interfaz en un contexto distinto de COM.  
  
 El código siguiente genera el error C3719:  
  
```  
// C3719a.cpp  
#define _ATL_ATTRIBUTES 1  
#include "atlbase.h"  
#include "atlcom.h"  
  
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];  
  
[object]  
__interface I {  
   HRESULT func1();  
};  
  
[event_source(native), coclass]  
struct A {  
   __event __interface I;   // C3719  
  
   // try the following line instead  
   // __event func2();  
};  
  
int main() {  
}  
```  
  
 Para resolver este error, aplique los atributos [object](../Topic/object%20\(C++\).md), [coclass](../../windows/coclass.md), [event\_source](../../windows/event-source.md) y [event\_receiver](../../windows/event-receiver.md) adecuadamente para convertir las clases donde utiliza la interfaz en clases COM.  Por ejemplo:  
  
```  
// C3719b.cpp  
#define _ATL_ATTRIBUTES 1  
#include <atlbase.h>  
#include <atlcom.h>  
  
[module(name="xx")];  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface I {  
   HRESULT f();  
};  
  
[coclass, event_source(com) , uuid("00000000-0000-0000-0000-000000000002")]  
struct MyStruct {  
   __event __interface I;  
};  
  
[event_receiver(com)]  
struct MyStruct2 {  
   void f() {  
   }  
   MyStruct2(I* pB) {  
      __hook(&I::f, pB, &MyStruct2::f);  
   }  
};  
  
int main()  
{  
}  
```