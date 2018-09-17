---
title: Dependencias acumuladas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dependencies, cumulative
- cumulative dependencies in NMAKE
- dependencies
ms.assetid: fa6dd777-80b8-437d-87a7-aec0ed818a49
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a66b153a52da06cca14845b9a58fcef0f42676d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725717"
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

[Destinos](../build/targets.md)