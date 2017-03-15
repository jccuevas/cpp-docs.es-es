---
title: "EXTERN (MASM) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "extern"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EXTERN directive"
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# EXTERN (MASM)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Define una o más variables externas, etiquetas, o símbolos denominados name cuyo tipo es `type`.  
  
## Sintaxis  
  
```  
  
   EXTERN [[langtype]] name [[(altid)]] :  
type [[, [[langtype]] name [[(altid)]] :type]]...  
```  
  
## Comentarios  
 `type` puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como constante.  Igual que [EXTRN](../../assembler/masm/extrn.md).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)