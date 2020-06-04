---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
api_name:
- _HUGE
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 3a0469b7158e765b1b1c6f34cb01c0e90beb1401
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940262"
---
# <a name="huge_val-_huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>Sintaxis

```
#include <math.h>
```

## <a name="remarks"></a>Comentarios

`HUGE_VAL` es el mayor valor doble que se puede representar. Muchas funciones matemáticas en tiempo de ejecución devuelven este valor cuando se produce un error. Para algunas funciones, se devuelve -`HUGE_VAL`. `HUGE_VAL` se define como `_HUGE`, pero las funciones matemáticas en tiempo de ejecución devuelven `HUGE_VAL`. También debe usar `HUGE_VAL` en el código para mantener la coherencia.

## <a name="see-also"></a>Vea también

[Constantes globales](../c-runtime-library/global-constants.md)
