---
title: "Error del compilador C3665 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3665"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3665"
ms.assetid: 893bb47e-8de1-43aa-af7d-fa47ad149ee9
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error del compilador C3665
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'destructor' : el especificador de reemplazo 'palabra clave' no se permite en un destructor\/finalizador  
  
 Se utilizó una palabra clave que no se permite en un destructor o finalizador.  
  
 Por ejemplo, no se puede solicitar una nueva ranura en un destructor o finalizador.  Para obtener más información, vea [Invalidaciones explícitas](../../windows/explicit-overrides-cpp-component-extensions.md) y [Destructores y finalizadores](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 El ejemplo siguiente genera el error C3665:  
  
```  
// C3665.cpp  
// compile with: /clr  
public ref struct R {  
   virtual ~R() { }  
   virtual void a() { }  
};  
  
public ref struct S : R {  
   virtual ~S() new {}   // C3665  
   virtual void a() new {}   // OK  
};  
```