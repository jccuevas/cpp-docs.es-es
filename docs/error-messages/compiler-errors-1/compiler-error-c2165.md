---
title: "Error del compilador C2165 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2165"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2165"
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2165
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'palabra clave': no se pueden modificar los punteros a datos  
  
 La palabra clave `__stdcall`, `__cdecl` o `__fastcall` intenta modificar un puntero a datos.  
  
 El ejemplo siguiente genera la advertencia C2165:  
  
```  
// C2165.cpp // compile with: /c char __cdecl *p;   // C2165 char *p;   // OK  
```