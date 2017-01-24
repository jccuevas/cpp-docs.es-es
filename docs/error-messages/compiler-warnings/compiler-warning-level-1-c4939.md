---
title: "Advertencia del compilador (nivel 1) C4939 | Microsoft Docs"
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
  - "C4939"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4939"
ms.assetid: 07096008-ba47-436c-a84c-2b03ad90d0b3
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4939
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma vtordisp está desusado y se quitará en una próxima versión de Visual C\+\+  
  
 Se quitará la pragma [vtordisp](../../preprocessor/vtordisp.md) en próximas versiones de Visual C\+\+  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4939:  
  
```  
// C4939.cpp // compile with: /c /W1 #pragma vtordisp(off)   // C4939  
```