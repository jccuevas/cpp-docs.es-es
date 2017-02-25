---
title: "ML Fatal Error A1007 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A1007"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A1007"
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Fatal Error A1007
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**nivel de anidamiento demasiado profundamente**  
  
 El ensamblador alcanzó el límite de anidamiento.  Tiene 20 niveles el límite excepto cuando conocido de otra manera.  
  
 Uno de los siguientes se están demasiado anidados:  
  
-   Una directiva de alto nivel como [.IF](../../assembler/masm/dot-if.md), [.REPEAT](../../assembler/masm/dot-repeat.md), o [.WHILE](../../assembler/masm/dot-while.md).  
  
-   Una definición de estructura.  
  
-   Una directiva de condicional\-ensamblado.  
  
-   una definición de procedimiento.  
  
-   una directiva de [PUSHCONTEXT](../../assembler/masm/pushcontext.md) \(el límite es 10\).  
  
-   Una definición del segmento.  
  
-   Un archivo de inclusión.  
  
-   una macro.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)