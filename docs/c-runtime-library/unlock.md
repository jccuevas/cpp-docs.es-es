---
title: _unlock
ms.date: 11/04/2016
api_name:
- _unlock
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unlock
- _unlock
helpviewer_keywords:
- unlock function
- _unlock function
ms.assetid: 2eda2507-a134-4997-aa12-f2f8cb319e14
ms.openlocfilehash: 73eec2b05b1d321bfc8ac61e743459bf2323fb8e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745113"
---
# <a name="_unlock"></a>_unlock

Libera un bloqueo multiproceso.

> [!IMPORTANT]
> Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.

## <a name="syntax"></a>Sintaxis

```cpp
void __cdecl _unlock(
   int locknum
);
```

#### <a name="parameters"></a>Parámetros

*locknum*<br/>
[in] El identificador del bloqueo que se liberará.

## <a name="requirements"></a>Requisitos

**Origen:** mlock.c

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_lock](../c-runtime-library/lock.md)
