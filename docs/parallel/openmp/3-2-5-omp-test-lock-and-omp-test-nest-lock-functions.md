---
title: 3.2.5 omp_test_lock y omp_test_nest_lock funciones | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5023f0b089d76e92be886f4917905f57dda7a018
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686232"
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock y omp_test_nest_lock (Funciones)
Estas funciones se intentan establecer un bloqueo, pero no impiden la ejecución del subproceso. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El argumento debe apuntar a una variable de bloqueo inicializado. Estas funciones se intentan establecer un bloqueo de la misma manera que `omp_set_lock` y `omp_set_nest_lock`, salvo que no bloqueen la ejecución del subproceso.  
  
 Un bloqueo simple, la `omp_test_lock` función devuelve un valor distinto de cero si el bloqueo se estableció correctamente; en caso contrario, devuelve cero.  
  
 Un bloqueo anidable, la `omp_test_nest_lock` función devuelve el recuento de anidamiento de nuevo si el bloqueo se estableció correctamente; en caso contrario, devuelve cero.