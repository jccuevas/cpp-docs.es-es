---
title: _fseek_nolock, _fseeki64_nolock
ms.date: 4/2/2020
api_name:
- _fseek_nolock
- _fseeki64_nolock
- _o__fseek_nolock
- _o__fseeki64_nolock
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fseek_nolock
- _fseeki64_nolock
- fseek_nolock
- fseeki64_nolock
helpviewer_keywords:
- _fseek_nolock function
- fseeki64_nolock function
- file pointers [C++], moving
- fseek_nolock function
- _fseeki64_nolock function
- seek file pointers
ms.assetid: 2dd4022e-b715-462b-b935-837561605a02
ms.openlocfilehash: 3533e7897e9c460d3be73b8907a6bd3c96f6888f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345732"
---
# <a name="_fseek_nolock-_fseeki64_nolock"></a>_fseek_nolock, _fseeki64_nolock

Mueve el puntero de archivo a una ubicación especificada.

## <a name="syntax"></a>Sintaxis

```C
int _fseek_nolock(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64_nolock(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>Parámetros

*Corriente*<br/>
Puntero a la estructura **FILE**.

*offset*<br/>
Número de bytes de *origin*.

*Origen*<br/>
Posición inicial.

## <a name="return-value"></a>Valor devuelto

Igual que [fseek](fseek-fseeki64.md) y [_fseeki64](fseek-fseeki64.md), respectivamente.

## <a name="remarks"></a>Observaciones

Estas funciones son las versiones sin bloqueo de [fseek](fseek-fseeki64.md) y [_fseeki64](fseek-fseeki64.md), respectivamente. Estos son idénticos a [fseek](fseek-fseeki64.md) y [_fseeki64](fseek-fseeki64.md) excepto que no están protegidos de interferencias por otros subprocesos. Es posible que estas funciones sean más rápidas porque no incurren en la sobrecarga de bloquear otros subprocesos. Use estas funciones solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fseek_nolock**, **_fseeki64_nolock**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
[Rebobinado](rewind.md)<br/>
