---
title: _lock
ms.date: 11/04/2016
api_name:
- _lock
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: 30cd84f008c7174d767ecf5e2b744a58b21e5000
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351095"
---
# <a name="_lock"></a>_lock

Adquiere un bloqueo multiproceso.

> [!IMPORTANT]
> Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.

## <a name="syntax"></a>Sintaxis

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Parámetros

*locknum*<br/>
[in] El identificador del bloqueo que se adquirirá.

## <a name="remarks"></a>Observaciones

Si ya se adquirió el bloqueo, este método obtiene el bloqueo de todas formas y produce un error interno en tiempo de ejecución de C (CRT). Si el método no puede adquirir un bloqueo, se cierra con un error irrecuperable y establece el código de error en `_RT_LOCK`.

## <a name="requirements"></a>Requisitos

**Origen:** mlock.c

## <a name="see-also"></a>Consulte también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
