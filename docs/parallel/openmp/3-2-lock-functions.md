---
title: 3.2 Funciones de bloqueo
ms.date: 11/04/2016
ms.assetid: 0ec855c6-55a9-49d7-bee4-5edae6e86a1b
ms.openlocfilehash: c189ba5b1f0bb365b387b4b4b887cfdb74d1bf2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573074"
---
# <a name="32-lock-functions"></a>3.2 Funciones de bloqueo

Las funciones descritas en esta sección manipulan los bloqueos que se usa para la sincronización.

Para las siguientes funciones, la variable de bloqueo debe tener tipo **omp_lock_t**. Esta variable solo debe obtenerse a través de estas funciones. Todas las funciones de bloqueo requieren un argumento que tiene un puntero a **omp_lock_t** tipo.

- El `omp_init_lock` función inicializa un bloqueo simple.

- El `omp_destroy_lock` función quita un bloqueo simple.

- El `omp_set_lock` función espera hasta que esté disponible un bloqueo simple.

- El `omp_unset_lock` función libera un bloqueo simple.

- El `omp_test_lock` función comprueba un bloqueo simple.

Para las siguientes funciones, la variable de bloqueo debe tener tipo **omp_nest_lock_t**.  Esta variable solo debe obtenerse a través de estas funciones. Todas las funciones de bloqueo anidable requieren un argumento que tiene un puntero a **omp_nest_lock_t** tipo.

- El `omp_init_nest_lock` función inicializa un bloqueo anidable.

- El `omp_destroy_nest_lock` función quita un bloqueo anidable.

- El `omp_set_nest_lock` función espera hasta que un bloqueo anidable está disponible.

- El `omp_unset_nest_lock` función libera un bloqueo anidable.

- El `omp_test_nest_lock` función comprueba un bloqueo anidable.

Las funciones de bloqueo de OpenMP tener acceso a la variable de bloqueo de manera que siempre lea y actualice el valor más reciente de la variable de bloqueo. Por lo tanto, no es necesaria para que un programa OpenMP incluir explícita **vaciar** directivas para garantizar que el valor de la variable de bloqueo es coherente entre diferentes subprocesos. (Es posible que sea necesario para **vaciar** directivas para que los valores de otras variables sean coherentes.)