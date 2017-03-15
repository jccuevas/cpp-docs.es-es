---
title: "Error irrecuperable C1020 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1020"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1020"
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error irrecuperable C1020
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#endif inesperada  
  
 Una directiva `#endif` no tiene una directiva `#if`, `#ifdef` o `#ifndef` coincidente. Asegúrese de que cada `#endif` tenga una directiva coincidente.  
  
 El ejemplo siguiente genera la advertencia C1020:  
  
```  
// C1020.cpp #endif     // C1020  
```  
  
 Posible solución:  
  
```  
// C1020b.cpp // compile with: /c #if 1 #endif  
```