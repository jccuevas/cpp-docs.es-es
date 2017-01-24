---
title: "Error del compilador C3253 | Microsoft Docs"
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
  - "C3253"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3253"
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3253
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : error con reemplazo explícito  
  
 Se ha especificado incorrectamente un reemplazo explícito.  Por ejemplo, no se puede especificar una implementación para un reemplazo que también se especifica como puro.  Para obtener más información, vea [Reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3253:  
  
```  
// C3253.cpp  
// compile with: /clr  
public interface struct I {  
   void a();  
   void b();  
   void c();  
};  
  
public ref struct R : I {  
   virtual void a() = 0, I::a {}   // C3253  
   virtual void b() = I::a {}   // OK  
   virtual void c() = 0;   // OK  
};  
```