---
title: "Advertencia del compilador C4957 | Microsoft Docs"
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
  - "C4957"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4957"
ms.assetid: a18c52d4-23e2-44f1-b4b5-f7fa5a7f3987
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4957
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'cast': la conversión explícita de 'cast\_from' a 'cast\_to' no es comprobable  
  
 Una conversión producirá una imagen no comprobable.  
  
 Algunas conversiones son seguras \(por ejemplo, un elemento `static_cast` que desencadena conversiones definidas por el usuario y un elemento `const_cast`\). Se garantiza que un elemento [safe\_cast](../../windows/safe-cast-cpp-component-extensions.md) genera código comprobable.  
  
 Para obtener más información, consulta [Código puro y comprobable](../../dotnet/pure-and-verifiable-code-cpp-cli.md).  
  
 Esta advertencia se emite como un error y se puede deshabilitar con la pragma [warning](../../preprocessor/warning.md) o la opción del compilador [\/wd](../../build/reference/compiler-option-warning-level.md).  
  
 El ejemplo siguiente genera la advertencia C4957:  
  
```  
// C4957.cpp // compile with: /clr:safe // #pragma warning( disable : 4957 ) using namespace System; int main() { Object ^ o = "Hello, World!"; String ^ s = static_cast<String^>(o);   // C4957 String ^ s2 = safe_cast<String^>(o);   // OK }  
```