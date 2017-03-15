---
title: "ML Nonfatal Error A2066 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2066"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2066"
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2066
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**modo incompatible de CPU y tamaño del segmento**  
  
 Se intentó abrir un segmento con **USE16**, **USE32**, o el atributo de **Plana** que no es compatible con CPU especificado, o cambiar a CPU de 16 bits mientras que en un segmento de 32 bits.  
  
 Los atributos de **USE32** y de **Plana** deben ir precedidas por el .386 o mayor de procesador de directivas.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)