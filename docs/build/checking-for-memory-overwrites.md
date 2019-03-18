---
title: Comprobar si se ha sobrescrito la memoria
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827704"
---
# <a name="checking-for-memory-overwrites"></a>Comprobar si se ha sobrescrito la memoria

Si se produce una infracción de acceso en una llamada a una función de manipulación del montón, es posible que el programa ha dañado el montón. Un síntoma común de esta situación sería:

```
Access Violation in _searchseg
```

El [_heapchk](../c-runtime-library/reference/heapchk.md) función está disponible en ambas versiones de depuración y lanzamiento (sólo en Windows NT) para comprobar la integridad del montón de biblioteca de tiempo de ejecución. Puede usar `_heapchk` en la misma manera que el `AfxCheckMemory` función para aislar una sobrescritura en el montón, por ejemplo:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Si esta función nunca se produce un error, debe aislar momento en que se ha dañado el montón.

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
