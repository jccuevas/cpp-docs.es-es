---
title: "Error del compilador C2161 | Microsoft Docs"
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
  - "C2161"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2161"
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2161
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\#\#' no puede aparecer al final de una definición de macro  
  
 Definición de macro que termina con un operador de pegado de token \(\#\#\).  
  
 El ejemplo siguiente genera el error C2161:  
  
```  
// C2161.cpp // compile with: /c #define mac(a,b) a   // OK #define mac(a,b) a##   // C2161  
```