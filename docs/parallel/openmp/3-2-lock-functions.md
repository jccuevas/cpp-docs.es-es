---
title: 3.2 funciones de bloqueo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd788b0ef1c72b1f38a44ee608ce0c7760e24adc
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="32-lock-functions"></a>3.2 Funciones de bloqueo
Las funciones descritas en esta sección manipulan los bloqueos utilizados para la sincronización.  
  
 Las siguientes funciones, la variable de bloqueo debe tener tipo **omp_lock_t**. Esta variable solo debe ser accesible a través de estas funciones. Todas las funciones de bloqueo requieren un argumento que tiene un puntero a **omp_lock_t** tipo.  
  
-   El `omp_init_lock` función inicializa un bloqueo simple.  
  
-   El `omp_destroy_lock` función quita un bloqueo simple.  
  
-   El `omp_set_lock` función espera hasta que un bloqueo simple está disponible.  
  
-   El `omp_unset_lock` función libera un bloqueo simple.  
  
-   El `omp_test_lock` función comprueba un bloqueo simple.  
  
 Las siguientes funciones, la variable de bloqueo debe tener tipo **omp_nest_lock_t**.  Esta variable solo debe ser accesible a través de estas funciones. Todas las funciones de bloqueo anidable requieren un argumento que tiene un puntero a **omp_nest_lock_t** tipo.  
  
-   El `omp_init_nest_lock` función inicializa un bloqueo anidable.  
  
-   El `omp_destroy_nest_lock` función quita un bloqueo anidable.  
  
-   El `omp_set_nest_lock` función espera hasta que un bloqueo anidable está disponible.  
  
-   El `omp_unset_nest_lock` función libera un bloqueo anidable.  
  
-   El `omp_test_nest_lock` función comprueba un bloqueo anidable.  
  
 Las funciones de bloqueo de OpenMP tener acceso a la variable de bloqueo de manera que siempre lea y actualice el valor más reciente de la variable de bloqueo. Por lo tanto, no es necesario para un programa de OpenMP debe incluir explícita **vaciar** directivas para garantizar que el valor de la variable de bloqueo es coherente entre subprocesos diferentes. (Puede haber una necesidad de **vaciar** directivas para que los valores de otras variables sean coherentes.)