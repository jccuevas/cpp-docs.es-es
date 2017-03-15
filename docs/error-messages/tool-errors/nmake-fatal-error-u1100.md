---
title: "Error grave de NMAKE U1100 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1100"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1100"
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error grave de NMAKE U1100
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la macro 'nombredemacro' no es válida en el contexto de la regla por lotes 'regla'  
  
 NMAKE genera este error cuando el bloque de comando de una regla por lotes directa o indirectamente hace referencia a una macro de archivo especial que no sea $\<.  
  
 $\< es la única macro permitida para las reglas por lotes.