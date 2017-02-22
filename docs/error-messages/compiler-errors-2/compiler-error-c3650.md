---
title: "Error del compilador C3650 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3650"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3650"
ms.assetid: ca4d8de4-b027-4d13-9b9f-03ca62905c33
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3650
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'interfaz\_método' : no se puede utilizar como reemplazo explícito, debe ser una función miembro virtual de una clase base  
  
 Se intentó realizar un reemplazo explícito en un miembro que no era virtual.  
  
 Para obtener más información, vea [Reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3650:  
  
```  
// C3650.cpp  
// compile with: /clr  
public interface struct I {  
   void a();  
};  
  
public ref class S {  
public:  
   static int f() { return 0; }  
   static int g() { return 0; }  
};  
  
public ref struct T1 : public S, I {  
   virtual int f() new sealed = S::f;   // C3650  
   virtual int g() { return 0; }   // OK does not override S::g  
   virtual void a() new sealed = I::a {}   // OK  
};  
```