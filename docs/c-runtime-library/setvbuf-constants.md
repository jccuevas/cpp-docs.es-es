---
title: "setvbuf (Constantes) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_IOFBF"
  - "_IONBF"
  - "_IOLBF"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_IOFBF (constante)"
  - "_IOLBF (constante)"
  - "_IONBF (constante)"
  - "IOFBF (constante)"
  - "IOLBF (constante)"
  - "IONBF (constante)"
ms.assetid: a6ec4dd5-1f24-498c-871a-e874cd28d33c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# setvbuf (Constantes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <stdio.h>  
  
```  
  
## Comentarios  
 Estas constantes representa el tipo de búfer para `setvbuf`.  
  
 Los valores posibles son clasificados por constantes de manifiesto siguientes:  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_IOFBF`|Almacenamiento en búfer completo: El búfer especificado en la llamada a `setvbuf` se utiliza y su tamaño es como se especifica en la llamada de `setvbuf` .  Si el puntero de búfer es **nulo**, el búfer automáticamente asignado del tamaño especificado se utiliza.|  
|`_IOLBF`|Igual que `_IOFBF`.|  
|`_IONBF`|No se utiliza ningún búfer, sin importar argumentos en la llamada a `setvbuf`.|  
  
## Vea también  
 [setbuf](../c-runtime-library/reference/setbuf.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)