---
title: "Advertencia del compilador (nivel 4) C4343 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4343"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4343"
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 4) C4343
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma optimize\("g",off\) invalida la opción \/Og  
  
 Esta advertencia, solo válida en el compilador de la familia de procesadores Itanium \(IPF\), informa de que una directiva pragma [optimize](../../preprocessor/optimize.md) reemplazó una opción del compilador [\/Og](../../build/reference/og-global-optimizations.md).  
  
 El ejemplo siguiente genera la advertencia C4343:  
  
```  
// C4343.cpp // compile with: /Og /W4 /LD // processor: IPF #pragma optimize ("g", off)   // C4343  
```