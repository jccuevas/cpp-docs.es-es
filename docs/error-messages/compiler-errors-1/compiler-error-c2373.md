---
title: "Error del compilador C2373 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2373"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2373"
ms.assetid: 7a08bf0b-852d-48be-ba75-70df9f4b5951
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C2373
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': nueva definición; modificadores de tipo distintos  
  
 El identificador ya está definido con un modificador de tipo diferente.  
  
 El ejemplo siguiente genera la advertencia C2373:  
  
```  
// C2373.h void __clrcall func( void ); const int i = 20;  
```  
  
 Y después:  
  
```  
// C2373.cpp // compile with: /c #include "C2373.h" extern void __cdecl func( void );   // C2373 extern void __clrcall func( void );   // OK extern int i;   // C2373 extern const int i;   // OK  
```