---
title: 3.2 funciones de bloqueo | Microsoft Docs
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
ms.openlocfilehash: 97f125129d4b35586111f3d4092d457560aaebec
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412280"
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