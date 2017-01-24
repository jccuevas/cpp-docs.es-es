---
title: "Error del compilador C2979 | Microsoft Docs"
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
  - "C2979"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2979"
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2979
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se admite especializaciones explícitas en genéricos  
  
 Se declaró una clase genérica incorrectamente.  Vea [Genéricos](../../windows/generics-cpp-component-extensions.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C2979.  
  
```  
// C2979.cpp // compile with: /clr /c generic <> ref class Utils {};   // C2979 error generic <class T> ref class Utils2 {};   // OK  
```