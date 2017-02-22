---
title: "Error del compilador C2585 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2585"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2585"
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C2585
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la conversión explícita a 'tipo' es ambigua  
  
 La conversión de tipos puede producir más de un resultado.  
  
### Posibles causas del error:  
  
1.  La conversión tiene lugar desde un tipo de clase o estructura basado en herencia múltiple.  Si el tipo hereda la misma clase base más de una vez, la función o el operador de conversión debe usar la resolución de ámbito \(`::`\) para especificar cuál de las clases heredadas se utilizará en la conversión.  
  
2.  Un operador de conversión y un constructor se han definido de manera que realizan la misma conversión.