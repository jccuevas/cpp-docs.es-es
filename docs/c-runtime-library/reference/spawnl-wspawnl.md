---
title: _spawnl, _wspawnl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wspawnl
- _spawnl
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
- spawnl
- wspawnl
- _wspawnl
- _spawnl
dev_langs:
- C++
helpviewer_keywords:
- spawnl function
- processes, creating
- _spawnl function
- processes, executing new
- _wspawnl function
- wspawnl function
- process creation
ms.assetid: dd4584c9-7173-4fc5-b93a-6e7d3c2316d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcd276e59edd78942f14211845c615d7e4f7eb6d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410725"
---
# <a name="spawnl-wspawnl"></a>_spawnl, _wspawnl

Crea y ejecuta un nuevo proceso.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _spawnl(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL
);
intptr_t _wspawnl(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>Parámetros

*mode*<br/>
Modo de ejecución para el proceso de llamada.

*CmdName*<br/>
Ruta de acceso del archivo que se va a ejecutar.

*arg0*, *arg1*,... *argn*<br/>
Lista de punteros a argumentos. El *arg0* argumento suele ser un puntero a *cmdname*. Los argumentos *arg1* a través de *argn* son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. Después de *argn*, debe haber un **NULL** puntero para marcar el final de la lista de argumentos.

## <a name="return-value"></a>Valor devuelto

El valor devuelto de un sincrónico **_spawnl** o **_wspawnl** (**_P_WAIT** especificado para *modo*) es el estado de salida del nuevo proceso. El valor devuelto de una asincrónica **_spawnl** o **_wspawnl** (**_P_NOWAIT** o **_P_NOWAITO** especificado para *modo* ) es el identificador de proceso. El estado de salida es 0 si el proceso finalizó normalmente. Puede establecer el estado de salida en un valor distinto de cero si el proceso generado llama específicamente a la **salir** rutina con un argumento distinto de cero. Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal con una anulación o una interrupción. Un valor devuelto de -1 indica un error (el nuevo proceso no se inicia). En este caso, **errno** se establece en uno de los siguientes valores.

|||
|-|-|
**E2BIG**|La lista de argumentos supera los 1024 bytes.
**EINVAL**|*modo* argumento no es válido.
**ENOENT**|El archivo o la ruta de acceso no se encuentra.
**ENOEXEC**|El archivo especificado no es ejecutable o no tiene un formato de archivo ejecutable válido.
**ENOMEM**|Memoria insuficiente para ejecutar el nuevo proceso.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Estas funciones validan sus parámetros. Si el valor *cmdname* o *arg0* es una cadena vacía o se invoca un puntero nulo, el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL**y devuelven -1. No se genera ningún proceso nuevo.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones crea y ejecuta un proceso nuevo, pasando cada argumento de la línea de comandos como parámetro independiente.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_spawnl**|\<process.h>|
|**_wspawnl**|\<stdio.h> o \<wchar.h>|

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
