---
title: _fflush_nolock
ms.date: 11/04/2016
api_name:
- _fflush_nolock
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fflush_nolock
- _fflush_nolock
helpviewer_keywords:
- fflush_nolock function
- _fflush_nolock function
- streams, flushing
- flushing
ms.assetid: 5e33c4a1-b10c-4001-ad01-210757919291
ms.openlocfilehash: f31ef5018abd9adbe9b9db00aaa91e3f0f0c01d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940974"
---
# <a name="_fflush_nolock"></a>_fflush_nolock

Vacía una secuencia sin bloquear el subproceso.

## <a name="syntax"></a>Sintaxis

```C
int _fflush_nolock(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Consulte [fflush](fflush.md).

## <a name="remarks"></a>Comentarios

Esta función es una versión que no es de bloqueo de **fflush**. Es idéntico a **fflush** , salvo que no está protegido frente a interferencias de otros subprocesos. Puede ser más rápidas porque no incurre en la sobrecarga de bloquear otros subprocesos. Use esta función solo en contextos seguros para subprocesos como aplicaciones de un único subproceso o donde el ámbito de llamada ya controle el aislamiento de subprocesos.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fflush_nolock**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fclose, _fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
