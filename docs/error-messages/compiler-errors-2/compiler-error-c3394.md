---
title: "Error del compilador C3394 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3394"
ms.assetid: 4e025d79-27ba-43c8-b0d9-839ecef98126
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis en la cláusula de restricciones: el 'identifier' encontrado esperaba un tipo  
  
 Había una restricción mal formada.  Para obtener más información, consulta [Restricciones de parámetros de tipo genérico \(C\+\+\/CLI\)](../Topic/Constraints%20on%20Generic%20Type%20Parameters%20\(C++-CLI\).md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3394:  
  
```  
// C3394.cpp // compile with: /clr /c ref class MyClass {}; ref class R { generic<typename T> where T : static   // C3394 // try the following line instead // where T : MyClass void f() {} };  
```