---
title: "Destinos de bloques de descripci&#243;n m&#250;ltiples | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bloques, descripción múltiple"
  - "bloques de descripción"
  - "bloques de descripciones múltiples"
ms.assetid: 8618dcd9-c11d-4562-91a7-0c904ed438a8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Destinos de bloques de descripci&#243;n m&#250;ltiples
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para actualizar un destino en varios bloques de descripción utilizando comandos diferentes, se han de especificar dos signos de dos puntos consecutivos \(::\) entre destinos y dependientes.  
  
```  
target.lib :: one.asm two.asm three.asm  
    ml one.asm two.asm three.asm  
    lib target one.obj two.obj three.obj  
target.lib :: four.c five.c  
    cl /c four.c five.c  
    lib target four.obj five.obj  
```  
  
## Vea también  
 [Destinos](../build/targets.md)