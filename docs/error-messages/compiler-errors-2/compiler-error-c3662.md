---
title: "Error del compilador C3662 | Microsoft Docs"
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
  - "C3662"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3662"
ms.assetid: 61bd3e41-a86b-42c0-be89-d992d3906ff1
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3662
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro': el especificador de invalidación 'especificador' solamente se permite en funciones miembro de clases administradas o de WinRT.  
  
 Se usó un especificador de invalidación en un miembro de tipo nativo, lo que no está permitido.  
  
 Para obtener más información, vea [Invalidaciones explícitas](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3662.  
  
```  
// C3662.cpp  
// compile with: /clr /c  
struct S {  
   virtual void f();  
};  
  
struct S1 : S {  
   virtual void f() new;   // C3662  
};  
  
ref struct T {  
   virtual void f();  
};  
  
ref struct T1 : T {  
   virtual void f() new;   // OK  
};  
```