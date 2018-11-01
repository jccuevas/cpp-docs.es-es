---
title: 4.4 OMP_NESTED
ms.date: 11/04/2016
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
ms.openlocfilehash: e45b8901c56923ab37ca387a5f057c5b41af21f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453630"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED

El `OMP_NESTED` variable de entorno habilita o deshabilita el paralelismo anidado a menos que el paralelismo anidado está habilitado o deshabilitado mediante una llamada a la `o` **mp_set_nested** rutina de biblioteca. Si establece en **TRUE**, paralelismo anidado está habilitado; si se establece en **FALSE**anidado paralelismo está deshabilitado. El valor predeterminado es **FALSE**.

Ejemplo:

```
setenv OMP_NESTED TRUE
```

## <a name="cross-reference"></a>Referencia cruzada:

- `omp_set_nested` función, vea [sección 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md) en la página 40.