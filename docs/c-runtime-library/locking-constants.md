---
title: "_locking (Constantes) | Microsoft Docs"
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
  - "_LK_RLCK"
  - "_LK_NBLCK"
  - "_LK_LOCK"
  - "_LK_NBRLCK"
  - "_LK_UNLCK"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_LK_LOCK (constante)"
  - "_LK_NBLCK (constante)"
  - "_LK_NBRLCK (constante)"
  - "_LK_RLCK (constante)"
  - "_LK_UNLCK (constante)"
  - "LK_LOCK (constante)"
  - "LK_NBLCK (constante)"
  - "LK_NBRLCK (constante)"
  - "LK_RLCK (constante)"
  - "LK_UNLCK (constante)"
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _locking (Constantes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## Comentarios  
 El argumento mode en la llamada a la función de `_locking` especifica la acción de bloqueo que se realizará.  
  
 El argumento *de modo* debe ser una de las constantes de manifiesto siguientes.  
  
 `_LK_LOCK`  
 Bloquea los bytes especificados.  Si los bytes no puede bloquear, la función intentarlo después de 1 segundo.  Si, después de 10 intentos, los bytes no puede bloquear, la función devuelve un error.  
  
 `_LK_RLCK`  
 Igual que `_LK_LOCK`.  
  
 `_LK_NBLCK`  
 Bloquea los bytes especificados.  Si los bytes no puede bloquear, la función devuelve un error.  
  
 `_LK_NBRLCK`  
 Igual que `_LK_NBLCK`.  
  
 `_LK_UNLCK`  
 Desbloquea los bytes especificados. \(Los bytes se deben haberse bloqueado previamente\).  
  
## Vea también  
 [\_locking](../c-runtime-library/reference/locking.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)