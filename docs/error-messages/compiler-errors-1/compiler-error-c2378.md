---
title: "Error del compilador C2378 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2378"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2378"
ms.assetid: 507a91c6-ca72-48df-b3a4-2cf931c86806
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2378
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': nueva definición; no se puede sobrecargar el símbolo con typedef  
  
 El identificador ya se ha redefinido como `typedef`.  
  
 El ejemplo siguiente genera la advertencia C2378:  
  
```  
// C2378.cpp // compile with: /c int i; typedef int i;   // C2378 typedef int b;   // OK  
```