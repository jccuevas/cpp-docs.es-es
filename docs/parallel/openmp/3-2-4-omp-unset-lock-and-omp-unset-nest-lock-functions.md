---
title: 3.2.4 omp_unset_lock y omp_unset_nest_lock funciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dc71c6c31a1d93b6e9c9cce2cd4f7830502a1a2f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="324-ompunsetlock-and-ompunsetnestlock-functions"></a>3.2.4 omp_unset_lock y omp_unset_nest_lock (Funciones)
Estas funciones proporcionan los medios de liberar la propiedad de un bloqueo. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_unset_lock(omp_lock_t *lock);  
void omp_unset_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El argumento de cada una de estas funciones debe apuntar a una variable inicializada bloqueo pertenece al subproceso que se ejecuta la función. El comportamiento es indefinido si el subproceso no pertenece ese bloqueo.  
  
 Un bloqueo simple, la `omp_unset_lock` función libera el subproceso que ejecuta la función de propiedad del bloqueo.  
  
 Un bloqueo anidable, la `omp_unset_nest_lock` funcionen disminuye el recuento de anidamiento y versiones el subproceso que ejecuta la función de propiedad del bloqueo, si el recuento resultante es cero.