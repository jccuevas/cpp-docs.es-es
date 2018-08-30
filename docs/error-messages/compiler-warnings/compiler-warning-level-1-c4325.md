---
title: Compilador advertencia (nivel 1) C4325 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd265938afb51cc402dc84f38b7e95188c6292a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197490"
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