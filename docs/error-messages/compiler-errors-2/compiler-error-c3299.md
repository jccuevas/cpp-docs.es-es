---
title: "Error del compilador C3299 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3299"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3299"
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error del compilador C3299
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member\_function': no puede especificar restricciones; estas se heredan del método base  
  
 Al reemplazar una función miembro genérica, no puede especificar cláusulas de restricción \(la repetición de las restricciones implica que las restricciones no se heredan\).  
  
 Se heredarán las cláusulas de restricción en la función genérica que está reemplazando.  
  
 Para obtener más información, consulta [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3299.  
  
```  
// C3299.cpp // compile with: /clr /c public ref struct R { generic<class T> where T : R virtual void f(); }; public ref struct S : R { generic<class T> where T : R   // C3299 virtual void f() override; };  
```