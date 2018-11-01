---
title: Bloques de descripción
ms.date: 11/04/2016
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: 214963b5c3f633e8d029cee0500d4bd5fab6ed53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490615"
---
# <a name="description-blocks"></a>Bloques de descripción

Un bloque de descripción es una línea de dependencia que opcionalmente puede ir seguida de un bloque de comandos:

```
targets... : dependents...
    commands...
```

Una línea de dependencia especifica uno o varios destinos y cero o más elementos dependientes. Debe ser un destino al principio de la línea. Se permiten los destinos se separan de los dependientes mediante dos puntos (:); espacios o tabulaciones. Para dividir la línea, use una barra diagonal inversa (\) después de un destino o dependientes. Si un destino no existe, tiene una marca de tiempo anterior a un dependiente, o es una [pseudodestino](../build/pseudotargets.md), NMAKE ejecuta los comandos. Si un dependiente es un destino en otra parte y no existe o no está actualizado con respecto a sus propios dependientes, NMAKE actualiza el dependiente antes de actualizar la dependencia actual.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Destinos](../build/targets.md)

[Dependientes](../build/dependents.md)

## <a name="see-also"></a>Vea también

[Referencia de NMAKE](../build/nmake-reference.md)