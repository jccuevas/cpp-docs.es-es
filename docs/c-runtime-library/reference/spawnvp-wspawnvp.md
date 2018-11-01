---
title: _spawnvp, _wspawnvp
ms.date: 11/04/2016
apiname:
- _wspawnvp
- _spawnvp
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wspawnvp
- _spawnvp
- wspawnvp
helpviewer_keywords:
- wspawnvp function
- processes, creating
- _wspawnvp function
- processes, executing new
- spawnvp function
- process creation
- _spawnvp function
ms.assetid: 8d8774ec-6ad4-4680-a5aa-440cde1e0249
ms.openlocfilehash: 5470c88ea0c39c421f027d219af5d3465324b1ff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649545"
---
# <a name="spawnvp-wspawnvp"></a>_spawnvp, _wspawnvp

Crea un proceso y lo ejecuta.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _spawnvp(
   int mode,
   const char *cmdname,
   const char *const *argv
);
intptr_t _wspawnvp(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parámetros

*mode*<br/>
Modo de ejecución para llamar al proceso.

*CmdName*<br/>
Ruta de acceso del archivo que se va a ejecutar.

*argv*<br/>
Matriz de punteros a argumentos. El argumento *argv*[0] suele ser un puntero a una ruta de acceso en modo real o al nombre del programa en modo protegido, y *argv*[1] a través de *argv*[**n**] son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. El argumento *argv*[**n** + 1] debe ser un **NULL** puntero para marcar el final de la lista de argumentos.

## <a name="return-value"></a>Valor devuelto

El valor devuelto de un valor sincrónico **_spawnvp** o **_wspawnvp** (**_P_WAIT** especificado para *modo*) es el estado de salida del nuevo proceso . El valor devuelto de asincrónico **_spawnvp** o **_wspawnvp** (**_P_NOWAIT** o **_P_NOWAITO** especificado para  *modo*) es el identificador de proceso. El estado de salida es 0 si el proceso finalizó normalmente. Puede establecer el estado de salida en un valor distinto de cero si el proceso generado usa específicamente un argumento distinto de cero para llamar a la **salir** rutina. Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal con una anulación o una interrupción. Un valor devuelto de -1 indica un error (no se inicia el proceso de nuevo). En este caso, **errno** se establece en uno de los siguientes valores:

|||
|-|-|
**E2BIG**|La lista de argumentos supera los 1024 bytes.
**EINVAL**|*modo* argumento no es válido.
**ENOENT**|El archivo o la ruta de acceso no se encuentra.
**ENOEXEC**|El archivo especificado no es ejecutable o no tiene un formato de archivo ejecutable válido.
**ENOMEM**|Memoria insuficiente para ejecutar el nuevo proceso.

Para obtener más información sobre estos y otros códigos de retorno, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cada una de estas funciones crea un nuevo proceso y lo ejecuta y se pasa una matriz de punteros a argumentos de línea de comandos y usa el **ruta** variable de entorno para buscar el archivo para ejecutar.

Estas funciones validan sus parámetros. Si bien *cmdname* o *argv* es un puntero nulo, o si *argv* apunta a un puntero nulo o *argv*[0] es una cadena vacía, el no válido se invoca el controlador de parámetros, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL**y devuelven -1. No se genera ningún proceso nuevo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_spawnvp**|\<stdio.h> o \<process.h>|
|**_wspawnvp**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Funciones _spawn y _wspawn](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
