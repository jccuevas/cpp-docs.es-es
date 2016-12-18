---
title: "Error del compilador C3461 | Microsoft Docs"
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
  - "C3461"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3461"
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3461
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': solamente se puede reenviar un tipo administrado  
  
 El reenvío de tipos solo puede realizarse con tipos CLR.  Vea [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md) para obtener más información.  
  
 Para obtener más información, consulta [Reenvío de tipos \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md).  
  
## Ejemplo  
 En el ejemplo siguiente se crea un componente.  
  
```  
// C3461.cpp // compile with: /clr /LD public ref class R {};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3461.  
  
```  
// C3461b.cpp // compile with: /clr /c #using "C3461.dll" class N {}; [assembly:TypeForwardedTo(N::typeid)];   // C3461 [assembly:TypeForwardedTo(R::typeid)];   // OK  
```