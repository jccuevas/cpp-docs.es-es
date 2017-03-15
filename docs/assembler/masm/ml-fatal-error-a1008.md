---
title: "ML Fatal Error A1008 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1008"
ms.assetid: fe592f9d-c37b-4cd8-a51d-e3c15ddcab83
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Fatal Error A1008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**anidamiento macro no**  
  
 Una macro no finalizó antes de que finalice el archivo o de [ENDM](../../assembler/masm/endm.md) de directivas que finalizaba se encuentra fuera de un bloque de la macro.  
  
 Una causa de este error es omisión de punto antes de [.REPEAT](../../assembler/masm/dot-repeat.md) o de [.WHILE](../../assembler/masm/dot-while.md).  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)