---
title: "Error del compilador C3297 | Microsoft Docs"
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
  - "C3297"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3297"
ms.assetid: 2a718b4c-6cdb-4418-92c0-fc3a259431c4
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3297
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'restricción\_2': no se puede usar 'restricción\_1' como restricción porque 'restricción\_1' tiene la restricción de valor  
  
 Las clases de valor son de tipo sealed. Si una restricción es una clase de valor, otra restricción nunca puede derivar de ella.  
  
 Para obtener más información, consulte [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3297.  
  
```  
// C3297.cpp // compile with: /clr /c generic<class T, class U> where T : value class where U : T   // C3297 public ref struct R {};  
```