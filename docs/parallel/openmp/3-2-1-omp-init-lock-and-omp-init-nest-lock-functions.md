---
title: "3.2.1 omp_init_lock and omp_init_nest_lock Functions | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.1 omp_init_lock and omp_init_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas funciones proporcionan el único medio de inicializar un bloqueo.  Cada función inicializa el bloqueo asociado al *bloqueo* de parámetros para el uso en llamadas subsiguientes.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El estado inicial se desbloquea \(es decir, ningún subproceso posee el bloqueo\).  Para un bloqueo encajable, el recuento inicial de anidamiento es cero.  No es compatible llamar a cualquiera de estas rutinas con una variable de bloqueo que se ha inicializado ya.