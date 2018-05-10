---
title: 3.2.3 omp_set_lock y omp_set_nest_lock funciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ba24e923051eb887db2a81c1d9765d31a4ef7b24
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="323-ompsetlock-and-ompsetnestlock-functions"></a>3.2.3 omp_set_lock y omp_set_nest_lock (Funciones)
Cada una de estas funciones bloquea el subproceso que ejecuta la función hasta que el bloqueo especificado está disponible y, a continuación, Establece el bloqueo. Un bloqueo simple está disponible si está desbloqueada. Un bloqueo anidable está disponible si está desbloqueada, o si ya tiene propietario por el subproceso que ejecuta la función. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_set_lock(omp_lock_t *lock);  
void omp_set_nest_lock(omp_nest_lock_t *lock);  
```  
  
 Un bloqueo simple, el argumento de la `omp_set_lock` función debe señalar a una variable de bloqueo inicializado. Propiedad del bloqueo se concede al subproceso de ejecución de la función.  
  
 Un bloqueo anidable, el argumento de la `omp_set_nest_lock` función debe señalar a una variable de bloqueo inicializado. Se incrementa el recuento de anidamiento, y el subproceso se concede o conserva, la propiedad del bloqueo.