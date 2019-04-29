---
title: Destinos múltiples
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
ms.openlocfilehash: 43e5216d5e11e89aff9b6f0c69ff4e76a8cc9da8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320973"
---
# <a name="multiple-targets"></a>Destinos múltiples

NMAKE evalúa varios destinos en una sola dependencia como si cada uno se ha especificado en un bloque de descripción independiente.

Por ejemplo, esto...

```Output
bounce.exe leap.exe : jump.obj
   echo Building...
```

.. .se evaluada como esto:

```Output
bounce.exe : jump.obj
   echo Building...
leap.exe : jump.obj
   echo Building...
```

## <a name="see-also"></a>Vea también

[Destinos](targets.md)
