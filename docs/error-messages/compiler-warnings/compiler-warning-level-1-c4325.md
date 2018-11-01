---
title: Advertencia del compilador (nivel 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 293cbbcfe134f6cb4f5e1bf924be7c03fa278833
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492614"
---
# <a name="compiler-warning-level-1-c4325"></a>Advertencia del compilador (nivel 1) C4325

> los atributos de sección estándar '*sección*' omite

## <a name="remarks"></a>Comentarios

No puede cambiar los atributos de una sección estándar. Por ejemplo:

```cpp
#pragma section(".sdata", long)
```

Esto sobrescribirá la `.sdata` sección estándar que utiliza el **corto** tipo de datos con el **largo** tipo de datos.

Incluyen secciones estándar cuyos atributos no pueden cambiar,

- .Data

- .sdata

- . BSS

- .sbss

- Text

- .const

- .sconst

- .rdata

- .srdata

Las secciones adicionales pueden agregarse más adelante.

## <a name="see-also"></a>Vea también

[section](../../preprocessor/section.md)