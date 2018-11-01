---
title: 3. Funciones de biblioteca en tiempo de ejecución
ms.date: 11/04/2016
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
ms.openlocfilehash: e1d8d498be7f58bcf510025c67c539127f450824
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484102"
---
# <a name="3-run-time-library-functions"></a>3. Funciones de biblioteca en tiempo de ejecución

Esta sección describen las funciones de biblioteca en tiempo de ejecución de OpenMP C y C++. El encabezado  **\<omp.h >** declara dos tipos, varias funciones que pueden usarse para controlar y consultar el entorno de ejecución en paralelo y bloquear las funciones que pueden utilizarse para sincronizar el acceso a datos.

El tipo **omp_lock_t** es un tipo de objeto puede representar que un bloqueo está disponible o que un subproceso posee un bloqueo. Estos bloqueos se conocen como *bloqueos simples*.

El tipo **omp_nest_lock_t** es un tipo de objeto puede representar que un bloqueo está disponible o la identidad del subproceso que posee el bloqueo y un *anidar recuento* (descrito a continuación). Estos bloqueos se conocen como *bloqueos anidables*.

Las funciones de biblioteca son funciones externas con vinculación de "C".

Las descripciones en este capítulo se dividen en los temas siguientes:

- Funciones de entorno de ejecución (consulte [sección 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) en página 35).

- Funciones de bloqueo (consulte [sección 3.2](../../parallel/openmp/3-2-lock-functions.md) en la página 41).