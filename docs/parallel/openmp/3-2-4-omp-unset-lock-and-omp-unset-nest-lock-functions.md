---
title: 3.2.4 omp_unset_lock y omp_unset_nest_lock funciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5357e43e-a7c0-41d7-b529-3f7d15da8b11
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f480a75efff737356c1477593e182537ae73a8c8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690226"
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