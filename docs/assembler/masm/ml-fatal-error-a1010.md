---
title: "ML Fatal Error A1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1010"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1010"
ms.assetid: 9e0b5241-67f4-4740-8701-3b2d2d1ad9e4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Fatal Error A1010
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**anidamiento no de bloque:**  
  
 Un principio del bloque no tenía coincidir realiza, o un final del bloque no tenía un principio coincidente.  Uno de los siguientes puede estar implicado:  
  
-   Una directiva de alto nivel como [.IF](../../assembler/masm/dot-if.md), [.REPEAT](../../assembler/masm/dot-repeat.md), o [.WHILE](../../assembler/masm/dot-while.md).  
  
-   Una directiva de condicional\-ensamblado como [IF &#91;SQL2008&#93;](../../assembler/masm/if-masm.md), [REPETICIÓN](../../assembler/masm/repeat.md), o **WHILE**.  
  
-   Una definición de estructura o unión.  
  
-   una definición de procedimiento.  
  
-   Una definición del segmento.  
  
-   una directiva de [POPCONTEXT](../../assembler/masm/popcontext.md) .  
  
-   Una directiva de condicional\-ensamblado, como [ELSE](../../assembler/masm/else-masm.md), [ELSEIF](../../assembler/masm/elseif-masm.md), o **ENDIF** sin [IF &#91;SQL2008&#93;](../../assembler/masm/if-masm.md)coincidente.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)