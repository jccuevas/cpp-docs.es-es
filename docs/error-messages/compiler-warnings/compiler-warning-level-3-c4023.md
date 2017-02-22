---
title: "Advertencia del compilador (nivel 3) C4023 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4023"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4023"
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 3) C4023
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo': el puntero con base se pasó a la función sin prototipo: número de parámetro  
  
 Si se pasa un puntero con base a una función sin prototipo, el puntero se normaliza, con resultados imprevisibles.  
  
 Para resolver esta advertencia, use funciones prototipo a las que se pasan punteros con base.