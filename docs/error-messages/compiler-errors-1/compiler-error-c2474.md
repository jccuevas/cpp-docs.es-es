---
title: "Error del compilador C2474 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2474"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2474"
ms.assetid: 64e6c61e-6e77-480e-bcf0-b30a2fc482ac
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# Error del compilador C2474
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'keyword': falta un punto y coma adyacente que podría ser una palabra clave o un identificador.  
  
 El compilador esperaba encontrar un punto y coma y no pudo determinar su intención. Agregue el punto y coma para solucionar este error.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2474.  
  
```  
// C2474.cpp // compile with: /clr /c ref class A { ref class B {} property int i;   // C2474 error }; // OK ref class B { ref class D {}; property int i; }; ref class E { ref class F {} property; int i; };  
```