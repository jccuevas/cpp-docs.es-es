---
title: "Advertencia del compilador (nivel 4) C4487 | Microsoft Docs"
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
  - "C4487"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4487"
ms.assetid: 796144cf-cd3c-4edc-b6a4-96192b7eb4f0
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4487
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función\_de\_clase\_derivada' : coincide el método no virtual heredado 'función\_de\_clase\_base' pero no está explícitamente marcado como 'new'  
  
 Una función de una clase derivada tiene la misma firma que una función de clase base no virtual.  C4487 le recuerda que la función de clase derivada no reemplaza la función de clase base.  Explícitamente marque la función de clase derivada como `new` para resolver esta advertencia.  
  
 Para obtener más información, vea [new \(nueva ranura en vtable\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4487.  
  
```  
// C4487.cpp  
// compile with: /W4 /clr  
using namespace System;  
public ref struct B {  
   void f() { Console::WriteLine("in B::f"); }  
   void g() { Console::WriteLine("in B::g"); }  
};  
  
public ref struct D : B {  
   void f() { Console::WriteLine("in D::f"); }   // C4487  
   void g() new { Console::WriteLine("in D::g"); }   // OK  
};  
  
int main() {  
   B ^ a = gcnew D;  
   // will call base class functions  
   a->f();  
   a->g();  
}  
```