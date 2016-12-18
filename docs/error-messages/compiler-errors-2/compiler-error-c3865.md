---
title: "Error del compilador C3865 | Microsoft Docs"
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
  - "C3865"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3865"
ms.assetid: 9bc62bb0-4fb8-4856-a5cf-c7cb4029a596
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3865
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'convención\_de\_llamada': solamente se puede utilizar en funciones miembro nativas  
  
 Se ha utilizado una convención de llamada en una función que era una función global o en una función miembro administrada.  La convención de llamada sólo se puede utilizar en una función miembro nativa \(no administrada\).  
  
 Para obtener más información, vea [Convenciones de llamada](../../cpp/calling-conventions.md).  
  
 El código siguiente genera el error C3865:  
  
```  
// C3865.cpp  
// compile with: /clr  
// processor: x86  
void __thiscall Func(){}   // C3865  
  
// OK  
struct MyType {  
   void __thiscall Func(){}  
};  
```