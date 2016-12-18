---
title: "Error del compilador C3274 | Microsoft Docs"
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
  - "C3274"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3274"
ms.assetid: 1f03f18e-b569-48eb-9249-11c70122a305
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3274
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_finally\/finally sin el correspondiente try  
  
 Se encontró una instrucción [\_\_finally](../../cpp/try-finally-statement.md) o [finally](../../dotnet/finally.md) sin un `try` correspondiente. Para resolver este problema, elimine la instrucción `__finally` o agregue una instrucción `try` para la instrucción `__finally`.  
  
 El ejemplo siguiente genera la advertencia C3274:  
  
```  
// C3274.cpp // compile with: /clr // C3274 expected using namespace System; int main() { try { try { throw gcnew ApplicationException(); } catch(...) { Console::Error->WriteLine(L"Caught an exception"); } finally { Console::WriteLine(L"In finally"); } } finally { Console::WriteLine(L"In finally"); } // Uncomment the following 3 lines to resolve. // try { //   throw gcnew ApplicationException(); // } finally { Console::WriteLine(L"In finally"); } Console::WriteLine(L"**FAIL**"); }  
```