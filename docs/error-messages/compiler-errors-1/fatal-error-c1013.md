---
title: "Error irrecuperable C1013 | Microsoft Docs"
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
  - "C1013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1013"
ms.assetid: 5514a679-efe7-4055-bdd3-5693ca0c332f
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador : hay demasiados paréntesis abiertos  
  
 Una expresión contiene demasiados niveles de paréntesis en una única expresión. Simplifique la expresión o divídala en varias instrucciones.  
  
 Antes de Visual C\+\+ 6.0 Service Pack 3, el límite de paréntesis anidados en una única expresión era 59. Actualmente, el límite de paréntesis anidados es 256.