---
title: "Error del compilador C3482 | Microsoft Docs"
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
  - "C3482"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3482"
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3482
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'this' solo se puede usar como captura lambda en una función miembro no estática  
  
 No se puede pasar `this` a la lista de captura de una expresión lambda declarada en un método estático o una función global.  
  
### Para corregir este error  
  
-   Convierta la función de inclusión a un método no estático, o  
  
-   Quite el puntero `this` de la lista de captura de la expresión lambda.  
  
## Ejemplo  
 El siguiente ejemplo genera el error C3482:  
  
```  
// C3482.cpp // compile with: /c class C { public: static void staticMethod() { [this] {}(); // C3482 } };  
```  
  
## Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)