---
title: "Error del compilador C3232 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3232"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3232"
ms.assetid: 3119b3a9-0eff-4a3f-b805-e4d160af9e39
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3232
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'parámetro': un parámetro de tipo genérico no se puede usar en un nombre completo  
  
 Se usó incorrectamente un parámetro de tipo genérico.  
  
 El ejemplo siguiente genera la advertencia C3232:  
  
```  
// C3232.cpp // compile with: /clr generic <class T> ref class C { typename T::TYPE t;   // C3232 };  
```