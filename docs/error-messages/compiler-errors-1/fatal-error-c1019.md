---
title: "Error irrecuperable C1019 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1019"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1019"
ms.assetid: c4f8968b-bc62-4200-b3ca-69d06c163236
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error irrecuperable C1019
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#else inesperada  
  
 La directiva `#else` aparece fuera de una construcción `#if`, `#ifdef` o `#ifndef`. Use `#else` solamente dentro de una de estas construcciones.  
  
 El ejemplo siguiente genera la advertencia C1019:  
  
```  
// C1019.cpp #else   // C1019 #endif int main() {}  
```  
  
 Posible solución:  
  
```  
// C1019b.cpp #if 1 #else #endif int main() {}  
```