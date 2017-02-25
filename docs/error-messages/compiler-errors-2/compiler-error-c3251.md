---
title: "Error del compilador C3251 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3251"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3251"
ms.assetid: 541c163e-5ee9-457c-a1e5-da860788b10d
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C3251
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede invocar el método de clase base en una instancia de tipo de valor  
  
 El siguiente error se produce porque `GetClass` es un miembro de `Microsoft.Runtime.Object`, no de `Microsoft.Runtime.Integer4`.