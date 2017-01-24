---
title: "Error del compilador C3825 | Microsoft Docs"
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
  - "C3825"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3825"
ms.assetid: 18e204a1-f26e-42c6-8d74-2b49cc95f940
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3825
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': una clase administrada o WinRT solo puede admitir eventos administrados o WinRT.  
  
 Solo los eventos .NET son compatibles con las clases administradas.  Solo los eventos de Windows en tiempo de ejecución son compatibles con las clases de Windows en tiempo de ejecución.  Para corregir este error en código administrado, cambie el parámetro de tipo de `event_source` y `event_receiver` de `native` a `managed`.  Otra solución sería quitar el atributo.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3825 y muestra cómo corregirlo:  
  
```  
// C3825a.cpp  
// compile with: /clr  
public delegate void del1();  
  
[event_source(native)]           // To fix, change 'native' to 'managed' or delete this line  
ref class CEventSrc  
{  
public:  
   event del1^ event1;       // C3825  
  
   void FireEvents() {  
      event1();  
   }  
};  
  
[event_receiver(native)]         // To fix, change 'native' to 'managed' or delete this line  
ref class CEventRec  
{  
public:  
   void handler1()  
   {  
      System::Console::WriteLine("Executing handler1().\n");  
   }  
   void HookEvents(CEventSrc^ pSrc)   
   {  
      pSrc->event1 += gcnew del1(this, &CEventRec::handler1);  
   }  
   void UnhookEvents(CEventSrc^ pSrc)   
   {  
      pSrc->event1 -= gcnew del1(this, &CEventRec::handler1);  
   }  
};  
  
int main()   
{  
   CEventSrc^ pEventSrc = gcnew CEventSrc;  
   CEventRec^ pEventRec = gcnew CEventRec;  
   pEventRec->HookEvents(pEventSrc);  
   pEventSrc->FireEvents();  
   pEventRec->UnhookEvents(pEventSrc);  
}  
```