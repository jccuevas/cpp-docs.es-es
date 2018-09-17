---
title: Buscando sobrescrituras en memoria | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- memory, overwrites
ms.assetid: da7c5d77-a267-415f-a8ab-ee5ce5bfc286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 246f625e899016080662f27a5901962c1c62f1a8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718657"
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