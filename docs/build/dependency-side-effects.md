---
title: Efectos secundarios de las relaciones de dependencia
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
ms.openlocfilehash: 4ce32a55e89d78d45bc74ce3f7dd45ff2f99af31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530057"
---
# <a name="dependency-side-effects"></a>Efectos secundarios de las relaciones de dependencia

Si se especifica un destino con un signo de dos puntos (:) en dos líneas de dependencia en diferentes ubicaciones y los comandos aparecen después de que solo uno de las líneas, NMAKE interpreta las dependencias como si adyacentes o combinadas. No se invoca una regla de inferencia para la dependencia que no tiene comandos, pero en su lugar se da por supuesto que las dependencias pertenecen a un bloque de descripción y ejecuta los comandos especificados con la otra dependencia. Por ejemplo, este conjunto de reglas:

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

se evalúa como esto:

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Este efecto no se produce si dos puntos dobles (`::`) se utiliza. Por ejemplo, este conjunto de reglas:

```Output
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

se evalúa como esto:

```Output
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

## <a name="see-also"></a>Vea también

[Destinos](../build/targets.md)