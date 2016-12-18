---
title: "Error del compilador C3648 | Microsoft Docs"
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
  - "C3648"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3648"
ms.assetid: 5d042989-41cb-4cd0-aa50-976b70146aaf
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3648
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta sintaxis de reemplazo explícita requiere \/clr:oldSyntax  
  
 Cuando compiló la última sintaxis administrada, el compilador encontró sintaxis de reemplazo explícito para versiones anteriores.  
  
 Para obtener más información, vea [Reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  Para obtener más información sobre la sintaxis más antigua, vea [Reemplazos explícitos](../../cpp/explicit-overrides-cpp.md).  
  
 El código siguiente genera el error C3648:  
  
```  
// C3648.cpp  
// compile with: /clr  
public interface struct I {  
   void f();  
};  
  
public ref struct R : I {  
   virtual void I::f() {}   // C3648  
   // try the following line instead  
   // virtual void f() = I::f{}  
};  
```