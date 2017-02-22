---
title: "Error del compilador C3400 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3400"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3400"
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# Error del compilador C3400
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

dependencia de restricción circular que implica 'constraint\_1' y 'constraint\_2'  
  
 El compilador detectó restricciones circulares.  
  
 Para obtener más información, consulta [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3400.  
  
```  
// C3400.cpp // compile with: /clr /c generic<class T, class U> where T : U where U : T   // C3400 public ref struct R {};  
```