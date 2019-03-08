---
title: Comprobar si se ha sobrescrito la memoria
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: b37bd68519aea1194b601e89fefd0f14d428630a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422200"
---
# <a name="checking-for-memory-overwrites"></a>Comprobar si se ha sobrescrito la memoria

Si se produce una infracción de acceso en una llamada a una función de manipulación del montón, es posible que el programa ha dañado el montón. Un síntoma común de esta situación sería:

```
Access Violation in _searchseg
```

El [_heapchk](../../c-runtime-library/reference/heapchk.md) función está disponible en ambas versiones de depuración y lanzamiento (sólo en Windows NT) para comprobar la integridad del montón de biblioteca de tiempo de ejecución. Puede usar `_heapchk` en la misma manera que el `AfxCheckMemory` función para aislar una sobrescritura en el montón, por ejemplo:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Si esta función nunca se produce un error, debe aislar momento en que se ha dañado el montón.

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](../../build/reference/fixing-release-build-problems.md)
