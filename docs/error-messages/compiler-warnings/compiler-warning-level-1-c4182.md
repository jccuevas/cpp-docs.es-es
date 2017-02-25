---
title: "Advertencia del compilador (nivel 1) C4182 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4182"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4182"
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 1) C4182
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El nivel de anidamiento \#include tiene una profundidad de 'número'; es posible que exista una recursividad infinita.  
  
 El compilador se quedó sin espacio en el montón debido al número de archivos de inclusión anidados. Un archivo de inclusión está anidado cuando se incluye desde otro archivo de inclusión.  
  
 Este mensaje es informativo y precede al error [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md).