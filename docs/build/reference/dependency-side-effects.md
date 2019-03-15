---
title: Efectos secundarios de las relaciones de dependencia
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, side effects
- NMAKE program, dependents
ms.assetid: d4e8db25-fdc0-4d73-81ec-1538f2e1b3e8
ms.openlocfilehash: b89306b6e4d85e0e08729fb1d35fb041d69647e7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827205"
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

[Destinos](targets.md)
