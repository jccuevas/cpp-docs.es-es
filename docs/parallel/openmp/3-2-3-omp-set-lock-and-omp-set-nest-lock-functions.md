---
title: 3.2.3 omp_set_lock y omp_set_nest_lock funciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: b5323879-f72e-418e-953f-3979fdda17a2
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e709e43a0b32b68bc34c4e76e8680ae371e30670
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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