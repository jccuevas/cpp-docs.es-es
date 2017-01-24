---
title: "Error del compilador C3830 | Microsoft Docs"
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
  - "C3830"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3830"
ms.assetid: c9798f88-5001-4067-9fb1-09957ddc6fa8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3830
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo1': no puede heredar de 'tipo2', los tipos de valor sólo pueden heredar de las clases de interfaz  
  
 Un tipo de valor no puede heredar una clase base.  Para obtener más información, vea [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3830:  
  
```  
// C3830a.cpp  
// compile with: /clr /c  
public value struct MyStruct4 {  
   int i;  
};  
  
public value class MyClass : public MyStruct4 {};   // C3830  
  
// OK  
public interface struct MyInterface4 {  
   void i();  
};  
  
public value class MyClass2 : public MyInterface4 {  
public:  
   virtual void i(){}  
};  
```  
  
 **Extensiones administradas de C\+\+**  
  
 Un tipo `__value` no puede heredar una clase base.  
  
 El código siguiente genera el error C3830:  
  
```  
// C3830b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
__value struct v : public System::Object {};   // C3830  
__value struct w {};   // OK  
```