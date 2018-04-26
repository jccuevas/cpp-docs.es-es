---
title: _spawnvpe, _wspawnvpe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _spawnvpe
- _wspawnvpe
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
- _spawnvpe
- wspawnvpe
- spawnvpe
- _wspawnvpe
dev_langs:
- C++
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b1498b5772386edb986d3bbd87c63b7c856a3c3
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="spawnvpe-wspawnvpe"></a>_spawnvpe, _wspawnvpe

Crea y ejecuta un nuevo proceso.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _spawnvpe(
   int mode,
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wspawnvpe(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parámetros

*mode*<br/>
Modo de ejecución para el proceso de llamada

*CmdName*<br/>
Ruta de acceso del archivo que se va a ejecutar

*argv*<br/>
Matriz de punteros a argumentos. El argumento *argv*[0] suele ser un puntero a una ruta de acceso en modo real o al nombre del programa en modo protegido, y *argv*[1] a través de *argv*[**n**] son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. El argumento *argv*[**n** + 1] debe ser un **NULL** puntero para marcar el final de la lista de argumentos.

*envp*<br/>
Matriz de punteros a la configuración del entorno

## <a name="return-value"></a>Valor devuelto

El valor devuelto de un sincrónico **_spawnvpe** o **_wspawnvpe** (**_P_WAIT** especificado para *modo*) es el estado de salida del nuevo proceso. El valor devuelto de una asincrónica **_spawnvpe** o **_wspawnvpe** (**_P_NOWAIT** o **_P_NOWAITO** especificado para  *modo*) es el identificador de proceso. El estado de salida es 0 si el proceso finalizó normalmente. Puede establecer el estado de salida en un valor distinto de cero si el proceso generado llama específicamente a la **salir** rutina con un argumento distinto de cero. Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal con una anulación o una interrupción. Un valor devuelto de -1 indica un error (el nuevo proceso no se inicia). En este caso, **errno** se establece en uno de los siguientes valores:

|||
|-|-|
**E2BIG**|La lista de argumentos supera los 1024 bytes.
**EINVAL**|*modo* argumento no es válido.
**ENOENT**|El archivo o la ruta de acceso no se encuentra.
**ENOEXEC**|El archivo especificado no es ejecutable o no tiene un formato de archivo ejecutable válido.
**ENOMEM**|Memoria insuficiente para ejecutar el nuevo proceso.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones crea y ejecuta un proceso nuevo, pasando una matriz de punteros a los argumentos de la línea de comandos y una matriz de punteros a la configuración del entorno. Estas funciones usan la **ruta de acceso** variable de entorno para buscar el archivo para ejecutar.

Estas funciones validan sus parámetros. Si el valor *cmdname* o *argv* es un puntero nulo, o si *argv* señala a un puntero nulo, o *argv*[0] es una cadena vacía, no válido se invoca el controlador de parámetros, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL**y devuelven -1. No se genera ningún proceso nuevo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h> o \<process.h>|
|**_wspawnvpe**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [Funciones _spawn y _wspawn](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Vea también

[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
