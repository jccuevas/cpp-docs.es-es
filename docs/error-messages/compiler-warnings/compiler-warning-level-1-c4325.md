---
title: Advertencia del compilador (nivel 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: e0a13761b0657d054065358994638779817dad6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163029"
---
# <a name="compiler-warning-level-1-c4325"></a>Advertencia del compilador (nivel 1) C4325

> se han omitido los atributos de la sección estándar '*sección*'

## <a name="remarks"></a>Observaciones

No puede cambiar los atributos de una sección estándar. Por ejemplo:

```cpp
#pragma section(".sdata", long)
```

Esto sobrescribiría la sección estándar `.sdata` que utiliza el tipo de datos **Short** con el tipo de datos **Long** .

Las secciones estándar cuyos atributos no se pueden cambiar son:

- .data

- .sdata

- . BSS

- .sbss

- .text

- . const

- .sconst

- . rdata

- .srdata

Se pueden agregar secciones adicionales más adelante.

## <a name="see-also"></a>Consulte también

[section](../../preprocessor/section.md)
