---
title: "Error del compilador C2473 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2473"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2473"
ms.assetid: 6bb7dbf5-b198-490f-860e-fd64d0c2a284
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error del compilador C2473
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': parece una definición de función, pero no hay ninguna lista de parámetros.  
  
 El compilador detectó lo que parecía una función, sin la lista de parámetros.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2473.  
  
```  
// C2473.cpp // compile with: /clr /c class A { int i {}   // C2473 }; class B { int i() {}   // OK };  
```