---
title: "Advertencia del compilador C4959 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4959"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4959"
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Advertencia del compilador C4959
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede definir la estructura no administrada 'type' en \/clr:safe porque el acceso a sus miembros proporciona código que no se puede comprobar  
  
 El acceso a un miembro de un tipo no administrado generará una imagen que no se puede comprobar \(peverify.exe\).  
  
 Para obtener más información, consulta [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [\/wd](../../build/reference/compiler-option-warning-level.md).  
  
 El ejemplo siguiente genera la advertencia C4959:  
  
```  
// C4959.cpp // compile with: /clr:safe // Uncomment the following line to resolve. // #pragma warning( disable : 4959 ) struct X { int data; }; int main() { X x; x.data = 10;   // C4959 }  
```