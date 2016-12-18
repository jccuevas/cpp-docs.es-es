---
title: "Error del compilador C2998 | Microsoft Docs"
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
  - "C2998"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2998"
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2998
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier': no puede ser una definición de plantilla  
  
 El compilador no pudo procesar la sintaxis usada en la definición de plantilla.  
  
 El ejemplo siguiente genera la advertencia C2998:  
  
```  
// C2998.cpp // compile with: /c template <class T> int x = 1018; // C2998  
```