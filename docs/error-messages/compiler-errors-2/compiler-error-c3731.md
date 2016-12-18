---
title: "Error del compilador C3731 | Microsoft Docs"
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
  - "C3731"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3731"
ms.assetid: 45f89fcd-464c-4bc8-8a42-edcb5416d26c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3731
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el evento 'función1' y el controlador 'función2' son incompatibles; el origen y el controlador de eventos deben ser del mismo tipo  
  
 El receptor del origen de eventos y eventos deben tener el mismo tipo \(por ejemplo `native` contra los tipos de `com` \).  Para resolver el error, haga coincidir el tipo del origen de eventos y el controlador de eventos.  
  
 El código siguiente genera el error C3731:  
  
```  
// C3731.cpp  
// compile with: /clr  
#using <mscorlib.dll>  
[event_source(native)]  
struct A {  
   __event void MyEvent();  
};  
  
[event_receiver(managed)]  
// try the following line instead  
// [event_receiver(native)]  
struct B {  
   void func();  
   B(A a) {  
      __hook(&A::MyEvent, &a, &B::func);   // C3731  
   }  
};  
  
int main() {  
}  
```