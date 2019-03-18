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
ms.openlocfilehash: eef065ac4fcedf13f3a5d54d4df0563fd04ef965
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750681"
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
