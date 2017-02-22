---
title: "Error del compilador C2289 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2289"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2289"
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2289
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el mismo calificador de tipo se ha utilizado más de una vez  
  
 Una definición o declaración de tipo utiliza un calificador de tipo \(`const`, `volatile`, `signed` o `unsigned`\) más de una vez, lo que provoca un error de compatibilidad con ANSI \(**\/Za**\).  
  
 El ejemplo siguiente genera la advertencia C2286:  
  
```  
// C2289.cpp // compile with: /Za /c volatile volatile int i;   // C2289 volatile int j;   // OK  
```