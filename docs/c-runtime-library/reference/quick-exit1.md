---
title: quick_exit1
ms.date: 11/04/2016
apiname:
- quick_exit
apilocation:
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 50f1ee72cce04c2bebc8f7396a2b6fad98301dd7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62358040"
---
# <a name="quickexit"></a>quick_exit

Provoca la finalización del programa normal.

## <a name="syntax"></a>Sintaxis

```C
__declspec(noreturn) void quick_exit(
    int status
);
```

### <a name="parameters"></a>Parámetros

*status*<br/>
El código de estado que se devolverá al entorno de host.

## <a name="return-value"></a>Valor devuelto

El **quick_exit** función no puede devolver al llamador.

## <a name="remarks"></a>Comentarios

El **quick_exit** función provoca la terminación normal del programa. Llama a ninguna función registrada por **atexit**, **_onexit** o señal controladores registrados por el **señal** función. Comportamiento es indefinido si **quick_exit** se llama más de una vez, o si el **salir** también se llama a la función.

El **quick_exit** llamadas a funciones, en el último en orden salir (LIFO), las funciones registradas por **at_quick_exit**, excepto para las funciones que ya se le llama cuando se registró la función.  El comportamiento es indefinido si se realiza una llamada [longjmp](longjmp.md) durante una llamada a una función registrada que finalizaría la llamada a la función.

Después de han llamado a las funciones registradas, **quick_exit** invoca **_Exit** utilizando el *estado* valor para devolver el control al entorno de host.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**quick_exit**|\<process.h> o \<stdlib.h>|

Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
