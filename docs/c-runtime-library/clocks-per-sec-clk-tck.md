---
title: CLOCKS_PER_SEC, CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: 40401028ef16f0d46baec92a37b2ba422d1e56ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621356"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC, CLK_TCK

## <a name="syntax"></a>Sintaxis

```

#include <time.h>
```

## <a name="remarks"></a>Comentarios

El tiempo en segundos es el valor devuelto por la función `clock`, dividido entre `CLOCKS_PER_SEC`. `CLK_TCK` es equivalente, pero se considera obsoleto.

## <a name="see-also"></a>Vea también

[clock](../c-runtime-library/reference/clock.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)