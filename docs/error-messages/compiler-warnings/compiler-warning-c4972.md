---
title: "Advertencia del compilador C4972 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4972"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4972"
ms.assetid: d18e8e65-b2ef-4d75-a207-fbd0c17c9060
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Advertencia del compilador C4972
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede comprobar la modificación o el tratamiento directo del resultado de una operación de conversión unbox como valor L  
  
 Si se desreferencia un controlador en un tipo de valor, que también conoce como conversión unboxing y después se asigna a él, no es comprobable.  
  
 Para obtener más información, consulta [Conversión boxing](../../windows/boxing-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4972.  
  
```  
// C4972.cpp // compile with: /clr:safe using namespace System; ref struct R { int ^ p;   // a value type }; int main() { R ^ r = gcnew R; *(r->p) = 10;   // C4972 // OK r->p = 10; Console::WriteLine( r->p ); Console::WriteLine( *(r->p) ); }  
```