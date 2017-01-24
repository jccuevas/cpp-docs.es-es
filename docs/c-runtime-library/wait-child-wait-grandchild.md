---
title: "_WAIT_CHILD, _WAIT_GRANDCHILD | Microsoft Docs"
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
  - "_WAIT_GRANDCHILD"
  - "WAIT_CHILD"
  - "WAIT_GRANDCHILD"
  - "_WAIT_CHILD"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_WAIT_CHILD (constante)"
  - "_WAIT_GRANDCHILD (constante)"
  - "WAIT_CHILD (constante)"
  - "WAIT_GRANDCHILD (constante)"
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _WAIT_CHILD, _WAIT_GRANDCHILD
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <process.h>  
  
```  
  
## Comentarios  
 La función de `_cwait` se puede usar en cualquier proceso para esperar cualquier otro proceso \(si se conoce el identificador de proceso\).  El argumento de acción puede tener uno de los valores siguientes:  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_WAIT_CHILD`|El proceso de llamada espera hasta que el nuevo proceso especificado finaliza.|  
|`_WAIT_GRANDCHILD`|El proceso de llamada espera hasta nuevo proceso especificado, y todos los procesos creados por ese nuevo proceso, finalizan.|  
  
## Vea también  
 [\_cwait](../c-runtime-library/reference/cwait.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)