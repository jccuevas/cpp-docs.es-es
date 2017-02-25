---
title: "Error del compilador C3379 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3379"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3379"
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3379
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase' : una clase anidada no puede tener un especificador de acceso al ensamblado como parte de su declaración  
  
 Cuando se aplica a un tipo administrado, como una clase o struct, las palabras clave [public](../../cpp/public-cpp.md) y [private](../../cpp/private-cpp.md) indican si la clase se expondrá a través de los metadatos del ensamblado.  `public` o `private` no se puede aplicar a una clase anidada, la cual heredará el acceso al ensamblado de la clase envolvente.  
  
 Al utilizarse con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md), las palabras clave `ref` y `value` indican que una clase es administrada \(vea [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md)\).  
  
 El código siguiente genera el error C3379:  
  
```  
// C3379a.cpp  
// compile with: /clr  
using namespace System;  
  
public ref class A {  
public:  
   static int i = 9;  
  
   public ref class BA {   // C3379  
   // try the following line instead  
   // ref class BA {  
   public:  
      static int ii = 8;  
   };  
};  
  
int main() {  
  
   A^ myA = gcnew A;  
   Console::WriteLine(myA->i);  
  
   A::BA^ myBA = gcnew A::BA;  
   Console::WriteLine(myBA->ii);  
}  
```  
  
 El código siguiente genera el error C3379:  
  
```  
// C3379b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
public __gc class A {  
public:  
   static int i = 9;  
  
   public __gc class BA {   // C3379  
   // try the following line instead  
   // __gc class BA {  
   public:  
      static int ii = 8;  
   };  
};  
  
int main() {  
  
   A *myA = new A;  
   Console::WriteLine(myA->i);  
  
   A::BA *myBA = new A::BA;  
   Console::WriteLine(myBA->ii);  
}  
```