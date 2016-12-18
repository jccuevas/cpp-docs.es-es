---
title: "ML Warning A4012 | Microsoft Docs"
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
  - "A4012"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A4012"
ms.assetid: 842b1259-9679-4eeb-a02d-672a583a94e5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ML Warning A4012
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**información de número de línea para el segmento sin el DISTRIBUIR de clases”**  
  
 Había instrucciones en un segmento que no tiene un nombre de clase que termina con “DISTRIBUIR.” El ensamblador no genera información CodeView para estas instrucciones.  
  
 CodeView no puede procesar los módulos con código en segmentos con los nombres de clase que no finalizan con “DISTRIBUIR.”  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)