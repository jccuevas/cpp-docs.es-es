---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: b1d9b099684d9671a60dd1afb1e6692e3c0d2a65
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220483"
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Sintaxis

```
#include <math.h>
```

## <a name="remarks"></a>Comentarios

`HUGE_VAL` es el mayor valor doble que se puede representar. Muchas funciones matemáticas en tiempo de ejecución devuelven este valor cuando se produce un error. Para algunas funciones, se devuelve -`HUGE_VAL`. `HUGE_VAL` se define como `_HUGE`, pero las funciones matemáticas en tiempo de ejecución devuelven `HUGE_VAL`. También debe usar `HUGE_VAL` en el código para mantener la coherencia.

## <a name="see-also"></a>Vea también

[Constantes globales](../c-runtime-library/global-constants.md)
