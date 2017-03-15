---
title: "3.2.4 omp_unset_lock and omp_unset_nest_lock Functions | Microsoft Docs"
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
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.4 omp_unset_lock and omp_unset_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas funciones proporcionan un medio de liberar la propiedad de un bloqueo.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El argumento de cada una de estas funciones debe señalar a una variable inicializada de bloqueo poseída por el subproceso que ejecuta la función.  el comportamiento es indefinido si el subproceso no posee ese bloqueo.  
  
 Para un bloqueo simple, libera de la función de `omp_unset_lock` el subproceso que ejecuta la función de la propiedad del bloqueo.  
  
 Para un bloqueo encajable, las disminuciones de la función de `omp_unset_nest_lock` el recuento de anidamiento, y libera el subproceso que ejecuta la función de la propiedad del bloqueo si el recuento resultante es cero.