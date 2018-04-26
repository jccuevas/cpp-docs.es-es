---
title: quick_exit1 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- quick_exit function
ms.assetid: ecfbdae6-01c4-45fa-aaeb-b368e1de2a9c
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fde06fc83b27b8bba43e3fa929cc8b97bb68dd06
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

El **quick_exit** función provoca la finalización normal del programa. No llama a ninguna función registrada por **atexit**, **_onexit** o controladores de señales registrados por el **señal** función. Comportamiento es indefinido si **quick_exit** se llama más de una vez, o si la **salir** también se llama la función.

El **quick_exit** llamadas a funciones, en el último en entrar en orden de salir (LIFO), las funciones registradas por **at_quick_exit**, excepto para las funciones que ya se llama cuando se registró la función.  El comportamiento es indefinido si se realiza una llamada [longjmp](longjmp.md) durante una llamada a una función registrada que finalizaría la llamada a la función.

Después de llamarse a las funciones registradas, **quick_exit** invoca **_Exit** mediante el uso de la *estado* valor para devolver el control al entorno de host.

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
