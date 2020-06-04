---
title: Comprobar si se ha sobrescrito la memoria
ms.date: 11/04/2016
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
ms.openlocfilehash: 2c59cb96d640df6dcd96b9e0eafbcd325ed475f5
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342252"
---
# <a name="checking-for-memory-overwrites"></a>Comprobar si se ha sobrescrito la memoria

Si se produce una infracción de acceso en una llamada a una función de manipulación de un montón, es posible que el programa haya dañado el montón. Un síntoma frecuente de esta situación sería:

```
Access Violation in _searchseg
```

La función [_heapchk](../c-runtime-library/reference/heapchk.md) está disponible en las compilaciones de depuración y de versión (solo Windows NT) para comprobar la integridad del montón de la biblioteca en tiempo de ejecución. Puede usar `_heapchk` de forma muy similar a la función `AfxCheckMemory` para aislar una sobrescritura del montón, por ejemplo:

```
if(_heapchk()!=_HEAPOK)
   DebugBreak();
```

Si alguna vez se produce un error en esta función, debe aislar en qué punto se ha dañado el montón.

## <a name="see-also"></a>Vea también

[Solucionar problemas de versiones de lanzamiento](fixing-release-build-problems.md)
