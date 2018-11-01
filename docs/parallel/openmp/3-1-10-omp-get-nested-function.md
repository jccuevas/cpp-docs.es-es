---
title: 3.1.10 omp_get_nested (Función)
ms.date: 11/04/2016
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
ms.openlocfilehash: a4db1e21f344f5cc58e2027b0816f9c8fb40b3bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519930"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested (Función)

El `omp_get_nested` función devuelve un valor distinto de cero si se habilita el paralelismo anidado y 0 si no lo está. Para obtener más información sobre el paralelismo anidado, vea la sección 3.1.9 en la página 40. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_nested(void);
```

Si una implementación no implementa paralelismo anidado, esta función siempre devuelve 0.