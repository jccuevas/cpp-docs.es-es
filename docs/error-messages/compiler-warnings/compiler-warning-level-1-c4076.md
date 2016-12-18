---
title: "Advertencia del compilador (nivel 1) C4076 | Microsoft Docs"
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
  - "C4076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4076"
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'typemod': no se puede utilizar con el tipo 'typename'  
  
 Un modificador de tipo, tanto si es **signed** como `unsigned`, no se puede usar con un tipo no entero.***typemod*** se omite.  
  
## Ejemplo  
 El ejemplo siguiente genera la advertencia C4076:  
  
```  
// C4076.cpp // compile with: /W1 /LD unsigned double x;   // C4076  
```