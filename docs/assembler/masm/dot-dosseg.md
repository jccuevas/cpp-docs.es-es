---
title: ".DOSSEG | Microsoft Docs"
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
  - ".DOSSEG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".DOSSEG directive"
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .DOSSEG
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Ordena los segmentos según la convención de segmentos de MS\-DOS: DISTRIBUIR primero, después segmentos no en DGROUP y, a continuación segmentos de DGROUP.  
  
## Sintaxis  
  
```  
  
.DOSSEG  
  
```  
  
## Comentarios  
 Los segmentos de DGROUP siguen este orden: segmentos no en BSS o la PILA, entonces segmentos de BSS y, finalmente segmentos de pila.  Se utiliza principalmente para asegurarse compatibilidad CodeView en programas independientes de MASM.  Igual que [DOSSEG](../../assembler/masm/dosseg.md).  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)