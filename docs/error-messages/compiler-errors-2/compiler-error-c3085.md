---
title: "Error del compilador C3085 | Microsoft Docs"
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
  - "C3085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3085"
ms.assetid: 1ac40bf2-f63e-439e-8921-47e6dadc8354
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constructor': un constructor no puede ser una 'palabra clave'  
  
 Un constructor se heredó incorrectamente. Vea [Especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3085.  
  
```  
// C3085.cpp // compile with: /c /clr ref struct S { S() abstract;   // C3085 S(S%) abstract;   // C3085 }; ref struct T { T() sealed {}   // C3085 T(T%) sealed {}   // C3085 };  
```