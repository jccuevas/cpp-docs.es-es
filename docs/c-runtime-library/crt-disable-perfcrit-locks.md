---
title: _CRT_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: 475cc57b5b47f5abf8c268db3acf9e727ce6a743
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593473"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

Deshabilita el bloqueo crítico para el rendimiento en las operaciones de E/S.

## <a name="syntax"></a>Sintaxis

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>Comentarios

La definición de este símbolo puede mejorar el rendimiento de programas enlazados a E/S uniproceso al forzar a todas las operaciones de E/S a asumir un modelo de E/S uniproceso. Para más información, vea [Rendimiento de bibliotecas multiproceso](../c-runtime-library/multithreaded-libraries-performance.md).

## <a name="see-also"></a>Vea también

[Constantes globales](../c-runtime-library/global-constants.md)