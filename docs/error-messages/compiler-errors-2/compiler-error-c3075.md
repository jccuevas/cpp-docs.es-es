---
title: "Error del compilador C3075 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3075"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3075"
ms.assetid: f431daa9-e0fa-48f0-a5c3-f99be96b55e3
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3075
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'instance': no puede insertar una instancia de un tipo de referencia \('type'\) en un tipo de valor  
  
 Un tipo de valor no puede contener una instancia de un tipo de referencia.  
  
 Para obtener más información, consulta [Semántica de pila de C\+\+ para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C3075.  
  
```  
// C3075.cpp // compile with: /clr /c ref struct U {}; value struct X { U y;   // C3075 }; ref struct Y { U y;   // OK };  
```