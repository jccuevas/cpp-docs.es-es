---
title: "Error del compilador C2845 | Microsoft Docs"
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
  - "C2845"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2845"
ms.assetid: 31b28ee9-978f-403b-94d8-dbaacd24cce0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2845
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : no se puede realizar aritmética con punteros en este tipo  
  
 No se puede incrementar el puntero a una clase administrada.  
  
 **Extensiones administradas de C\+\+**  
  
 No se puede incrementar el puntero a una clase [\_\_gc](../../misc/gc.md).  Además, los operadores de cadena sólo son válidos con **\/clr** \(no con **\/clr:oldSyntax**\).  
  
 El código siguiente genera el error C2845:  
  
```  
// C2845b.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
__gc class X {};  
  
int main() {  
   X *pX = new X;  
   pX++;   // C2845  
  
   String * a = new String("abc");  
   String * b = new String("def");  
   Console::WriteLine(a + b);   // C2845 not with /clr:oldSyntax  
}  
```