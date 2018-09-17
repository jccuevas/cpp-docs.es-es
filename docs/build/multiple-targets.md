---
title: Varios destinos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- makefiles, targets
- multiple targets in NMAKE
- targets, multiple in NMAKE
- NMAKE program, targets
ms.assetid: b609a179-0b9f-4b08-9930-998047588ae0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66849bdbe28ac2bd965714de56f962df98ced133
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703669"
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

[Destinos](../build/targets.md)