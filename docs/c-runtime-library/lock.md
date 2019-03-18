---
title: _lock
ms.date: 11/04/2016
apiname:
- _lock
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- lock
- _lock
helpviewer_keywords:
- lock function
- _lock function
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
ms.openlocfilehash: d29488c6dec15fb58eef24f50c1bfafefb8e85c6
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741145"
---
# <a name="lock"></a>_lock

Adquiere un bloqueo multiproceso.

> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.

## <a name="syntax"></a>Sintaxis

```
void __cdecl _lock
   int locknum
);
```

#### <a name="parameters"></a>Parámetros

*locknum*<br/>
[in] El identificador del bloqueo que se adquirirá.

## <a name="remarks"></a>Comentarios

Si ya se adquirió el bloqueo, este método obtiene el bloqueo de todas formas y produce un error interno en tiempo de ejecución de C (CRT). Si el método no puede adquirir un bloqueo, se cierra con un error irrecuperable y establece el código de error en `_RT_LOCK`.

## <a name="requirements"></a>Requisitos

**Origen:** mlock.c

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[_unlock](../c-runtime-library/unlock.md)
