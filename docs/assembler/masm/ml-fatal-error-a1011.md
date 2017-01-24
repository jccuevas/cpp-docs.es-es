---
title: "ML Fatal Error A1011 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1011"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1011"
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Fatal Error A1011
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**la directiva debe estar en un bloque de control**  
  
 El ensamblador encontró una directiva de alto nivel donde no se esperaba uno.  Una de las siguientes directivas se encontró:  
  
-   [.ELSE](../../assembler/masm/dot-else.md) sin [.IF](../../assembler/masm/dot-if.md)  
  
-   [.ENDIF](../../assembler/masm/dot-endif.md) sin [.IF](../../assembler/masm/dot-if.md)  
  
-   [.ENDW](../../assembler/masm/dot-endw.md) sin [.WHILE](../../assembler/masm/dot-while.md)  
  
-   [.UNTILCXZ](../../assembler/masm/dot-untilcxz.md) sin [.REPEAT](../../assembler/masm/dot-repeat.md)  
  
-   [.CONTINUE](../../assembler/masm/dot-continue.md) sin [.WHILE](../../assembler/masm/dot-while.md) o [.REPEAT](../../assembler/masm/dot-repeat.md)  
  
-   [.BREAK](../../assembler/masm/dot-break.md) sin [.WHILE](../../assembler/masm/dot-while.md) o [.REPEAT](../../assembler/masm/dot-repeat.md)  
  
-   [.ELSE](../../assembler/masm/dot-else.md) después de `.ELSE`  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)