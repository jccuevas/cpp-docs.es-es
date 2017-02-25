---
title: "Error del compilador C3496 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3496"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3496"
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3496
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'this' siempre se captura por valor: se ha omitido '&'  
  
 No se puede capturar el `this` puntero por referencia.  
  
### Para corregir este error  
  
-   Capture el puntero `this` por valor.  
  
## Ejemplo  
 El ejemplo siguiente genera C3496 porque una referencia al puntero `this` aparece en la lista de captura de una expresión lambda:  
  
```  
// C3496.cpp // compile with: /c class C { void f() { [&this] {}(); // C3496 } };  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)