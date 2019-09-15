---
title: quick_exit1
ms.date: 11/04/2016
api_name:
- quick_exit
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- quick_exit
- process/quick_exit
- stdlib/quick_exit
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
ms.openlocfilehash: 86246ed7a32dcd2f12b38aa4148570fc5fb3b7a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949669"
---
# <a name="quick_exit"></a>quick_exit

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

La función **quick_exit** no puede volver a su llamador.

## <a name="remarks"></a>Comentarios

La función **quick_exit** provoca la finalización del programa normal. No llama a ninguna función registrada por los controladores **AtExit**, **_onexit** o Signal registrados por la función **Signal** . El comportamiento es indefinido si se llama a **quick_exit** más de una vez, o si también se llama a la función **Exit** .

La función **quick_exit** llama a, en orden LIFO (último en salir, primero en salir), las funciones registradas por **at_quick_exit**, excepto las funciones a las que ya se ha llamado cuando se registró la función.  El comportamiento es indefinido si se realiza una llamada [longjmp](longjmp.md) durante una llamada a una función registrada que finalizaría la llamada a la función.

Después de llamar a las funciones registradas, **quick_exit** invoca **_Exit** con el valor de *Estado* para devolver el control al entorno de host.

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
