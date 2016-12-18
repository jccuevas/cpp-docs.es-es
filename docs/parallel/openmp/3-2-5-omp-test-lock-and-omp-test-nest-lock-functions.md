---
title: "3.2.5 omp_test_lock and omp_test_nest_lock Functions | Microsoft Docs"
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
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.2.5 omp_test_lock and omp_test_nest_lock Functions
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Estas funciones intentan establecer un bloqueo pero no bloquean la ejecución de subprocesos.  El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El argumento debe señalar a una variable inicializada de bloqueo.  Estas funciones intentan establecer un bloqueo de la misma manera que `omp_set_lock` y `omp_set_nest_lock`, salvo que no bloquean la ejecución de subprocesos.  
  
 Para un bloqueo simple, la función de `omp_test_lock` devuelve un valor distinto de cero si el bloqueo se establece correctamente; de lo contrario, devuelve cero.  
  
 Para un bloqueo encajable, la función de `omp_test_nest_lock` devuelve el nuevo número de anidamiento si el bloqueo se establece correctamente; de lo contrario, devuelve cero.