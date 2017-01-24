---
title: "Error irrecuperable C1022 | Microsoft Docs"
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
  - "C1022"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1022"
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1022
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se esperaba \#endif  
  
 Una directiva `#if`, `#ifdef` o `#ifndef` no tiene una directiva `#endif` coincidente. Asegúrese de que cada `#if`, `#ifdef` o `#ifndef` tenga una `#endif` coincidente.  
  
 El ejemplo siguiente genera la advertencia C1022:  
  
```  
// C1022.cpp #define true 1 #if (true) #else #else    // C1022  
```  
  
 Posible resolución:  
  
```  
// C1022b.cpp // compile with: /c #define true 1 #if (true) #else #endif  
```