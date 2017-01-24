---
title: "Error del compilador C2465 | Microsoft Docs"
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
  - "C2465"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2465"
ms.assetid: 65ba2a9f-d95e-4af3-b60b-1ac59a1e307c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2465
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede definir un tipo anónimo entre paréntesis  
  
 Una estructura anónima, una unión o un tipo enumerado están definidos dentro de una expresión entre paréntesis. Esto no es válido en C\+\+ porque la definición no tiene sentido en el ámbito de la función.