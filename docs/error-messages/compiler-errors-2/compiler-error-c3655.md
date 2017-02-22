---
title: "Error del compilador C3655 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3655"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3655"
ms.assetid: 724919ab-2915-4b61-8794-44648e162d62
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3655
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : la función ya se ha reemplazado explícitamente  
  
 Una función sólo se puede reemplazar explícitamente una vez.  Para obtener más información, vea [Reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3655:  
  
```  
// C3655.cpp  
// compile with: /clr /c  
public ref struct B {  
   virtual void f();  
   virtual void g();  
};  
  
public ref struct D : B {  
   virtual void f() new sealed = B::f;  
   virtual void g() new sealed = B::f;   // C3655  
   // try the following line instead  
   // virtual void g() new sealed = B::g;  
};  
```