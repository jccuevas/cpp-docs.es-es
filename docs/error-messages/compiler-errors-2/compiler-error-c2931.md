---
title: "Error del compilador C2931 | Microsoft Docs"
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
  - "C2931"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2931"
ms.assetid: 33430407-b149-4ba3-baf8-b0dae1ea3a5d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2931
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'class': el identificador de clase de tipo redefinido como una función miembro de 'identifier'  
  
 No puede usar una clase genérica o de plantilla como una función miembro de otra clase.  
  
 Este error puede producirse si las llaves no coinciden como es debido.  
  
 El ejemplo siguiente genera la advertencia C2931:  
  
```  
// C2931.cpp // compile with: /c template<class T> struct TC { }; struct MyStruct { void TC<int>();   // C2931 }; struct TC2 { }; struct MyStruct2 { void TC2(); };  
```  
  
 También se puede producir C2931 al usar genéricos:  
  
```  
// C2931b.cpp // compile with: /clr /c generic<class T> ref struct GC {}; struct MyStruct { void GC<int>();   // C2931 void GC2();   // OK };  
```