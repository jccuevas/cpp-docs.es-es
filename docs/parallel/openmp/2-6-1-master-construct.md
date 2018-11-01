---
title: 2.6.1 master (Construcción)
ms.date: 11/04/2016
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
ms.openlocfilehash: 0501b1fdfbd36829cee2793fc0f7bb03daeda900
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475535"
---
# <a name="261-master-construct"></a>2.6.1 master (Construcción)

El **maestro** directiva identifica una construcción que especifica un bloque estructurado que se ejecuta el subproceso principal del equipo. La sintaxis de la **maestro** directiva es como sigue:

```
#pragma omp master new-linestructured-block
```

Otros subprocesos en el equipo no ejecuten el bloque estructurado asociado. No hay ninguna barrera implícita ya sea en la entrada o salida de la construcción principal.