---
title: "Error del compilador C3493 | Microsoft Docs"
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
  - "C3493"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3493"
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3493
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var' no se puede capturar de forma implícita porque no se ha especificado ningún modo de captura predeterminado  
  
 La captura de la expresión lambda vacía, `[]`, especifica que la expresión lambda no captura de forma explícita ni implícita ninguna variable.  
  
### Para corregir este error  
  
-   Proporcione un modo de captura predeterminado, o bien  
  
-   Capture explícitamente una o varias variables.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3493 porque modifica una variable externa, pero especifica la cláusula de captura vacía:  
  
```  
// C3493a.cpp int main() { int m = 55; [](int n) { m = n; }(99); // C3493 }  
```  
  
## Ejemplo  
 El ejemplo siguiente resuelve el error C3493 especificando mediante referencia como el modo de captura predeterminado.  
  
```  
// C3493b.cpp int main() { int m = 55; [&](int n) { m = n; }(99); }  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)