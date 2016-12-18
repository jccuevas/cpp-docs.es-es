---
title: "Error del compilador C2042 | Microsoft Docs"
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
  - "C2042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2042"
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2042
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

las palabras clave signed\/unsigned se excluyen mutuamente  
  
 Las palabras clave `signed` y `unsigned` se usan en una sola declaración.  
  
 El ejemplo siguiente genera la advertencia C2042.  
  
```  
// C2042.cpp unsigned signed int i;   // C2042  
```  
  
 Posible solución:  
  
```  
// C2042b.cpp // compile with: /c unsigned int i; signed int ii;  
```