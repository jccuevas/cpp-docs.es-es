---
title: Dependencias acumuladas
ms.date: 11/04/2016
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
ms.openlocfilehash: de0a9649be8f0dae58f45d8980d2df610ff2febe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57826352"
---
# <a name="cumulative-dependencies"></a>Dependencias acumuladas

Las dependencias son acumulativas en un bloque de descripción, si se repite un destino.

Por ejemplo, este conjunto de reglas,

```Output
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

se evalúa como esto:

```Output
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Varios destinos en varias líneas de dependencia en un bloque de descripción solo se evalúan como si cada uno se han especificado en un bloque de descripción independiente, pero los destinos que no están en la última línea de dependencia no usan el bloque de comandos. NMAKE intenta usar una regla de inferencia para estos destinos.

Por ejemplo, este conjunto de reglas,

```Output
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

se evalúa como esto:

```Output

leap.exe : jump.obj
# invokes an inference rule
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
climb.exe : up.obj
   echo Building bounce.exe...
```

## <a name="see-also"></a>Vea también

[Destinos](targets.md)
