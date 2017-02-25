---
title: "ML Nonfatal Error A2133 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "A2133"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "A2133"
ms.assetid: 5ba50911-22c8-43b7-90e2-946fc612e05f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# ML Nonfatal Error A2133
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**valor del registro sobrescriba INVOKE**  
  
 Un registro se ha pasado como argumento a un procedimiento, pero el código generado por [INVOCAR](../../assembler/masm/invoke.md) para pasar otros argumentos destruyó el contenido del registro.  
  
 El AX, ESTÉ, los registros AH, de, EAX de DX, de DL, de ADO, y de EDX se puede utilizar para el ensamblador para realizar la conversión de datos.  
  
 Utilice un registro diferente.  
  
## Vea también  
 [ML Error Messages](../../assembler/masm/ml-error-messages.md)