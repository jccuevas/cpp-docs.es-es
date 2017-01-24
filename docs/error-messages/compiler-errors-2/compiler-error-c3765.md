---
title: "Error del compilador C3765 | Microsoft Docs"
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
  - "C3765"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3765"
ms.assetid: feadee7a-fcfb-402c-af2f-0e656f814a13
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3765
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'evento': no se puede definir un evento en una class\/struct 'tipo' marcada como event\_receiver  
  
 Si una clase está marcada con el atributo [event\_receiver](../../windows/event-receiver.md), no puede contener una declaración [\_\_event](../../cpp/event.md).  
  
 El código siguiente genera el error C3765:  
  
```  
// C3765.cpp  
[event_receiver(native)]  
struct ER2 {  
   __event void f();   // C3765  
   __event void b(int);   // C3765  
};  
```