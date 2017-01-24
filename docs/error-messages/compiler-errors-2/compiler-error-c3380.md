---
title: "Error del compilador C3380 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3380"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3380"
ms.assetid: 86f1f4ec-4ad8-4a1a-9b6c-2d9b6129df6b
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3380
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': especificador de acceso de ensamblado no válido; solo se permiten 'public' o 'private'  
  
 Cuando se aplican a una clase o estructura administrada, las palabras clave [public](../../cpp/public-cpp.md) y [private](../../cpp/private-cpp.md) indican si la clase se expondrá a través de los metadatos del ensamblado. Solo `public` o `private` pueden aplicarse a una clase en un programa compilado con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 Las palabras clave `ref` y `value`, cuando se usan con [\/clr](../../build/reference/clr-common-language-runtime-compilation.md), indican que una clase es administrada \(vea [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md)\).  
  
 El ejemplo siguiente genera la advertencia C3380:  
  
```  
// C3380_2.cpp // compile with: /clr protected ref class A {   // C3380 // try the following line instead // ref class A { public: static int i = 9; }; int main() { A^ myA = gcnew A; System::Console::WriteLine(myA->i); }  
```  
  
 El ejemplo siguiente genera la advertencia C3380:  
  
```  
// C3380.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> protected __gc class A {   // C3380 // try the following line instead // __gc class A { public: static int i = 9; }; int main() { A *myA = new A; Console::WriteLine(myA->i); }  
```