---
title: 3.2 funciones de bloqueo | Documentos de Microsoft
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
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 151c809a7bd28a2e4384371f5cec3bd192eed9d1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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