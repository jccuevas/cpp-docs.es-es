---
title: "Error del compilador C3909 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3909"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3909"
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3909
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una declaración de evento WinRT o administrado debe tener lugar en un tipo WinRT o administrado  
  
 Se declaró un evento de Windows en tiempo de ejecución o administrado en un tipo nativo.  Para corregir este error, declare los eventos en tipos de Windows en tiempo de ejecución o en tipos administrados.  
  
 Para obtener más información, vea [evento](../../windows/event-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera el error C3909 y muestra cómo corregirlo:  
  
```  
// C3909.cpp  
// compile with: /clr /c  
delegate void H();  
class X {  
   event H^ E;   // C3909 - use ref class X instead  
};  
  
ref class Y {  
   static event H^ E {  
      void add(H^) {}  
      void remove( H^ h ) {}  
      void raise( ) {}  
   }  
};  
```