---
title: _spawnvpe, _wspawnvpe
ms.date: 11/04/2016
api_name:
- _spawnvpe
- _wspawnvpe
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _spawnvpe
- wspawnvpe
- _wspawnvpe
helpviewer_keywords:
- _wspawnvpe function
- processes, creating
- _spawnvpe function
- processes, executing new
- wspawnvpe function
- process creation
- spawnvpe function
ms.assetid: 3db6394e-a955-4837-97a1-fab1db1e6092
ms.openlocfilehash: 1ea71f5d7a9cd640e3d314eb48846bca995dca5c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442698"
---
# <a name="_spawnvpe-_wspawnvpe"></a>_spawnvpe, _wspawnvpe

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

*cmdname*<br/>
Ruta de acceso del archivo que se va a ejecutar

*argv*<br/>
Matriz de punteros a argumentos. El argumento *argv*[0] suele ser un puntero a una ruta de acceso en modo real o al nombre del programa en modo protegido, y *argv*[1] a *argv*[**n**] son punteros a las cadenas de caracteres que forman la nueva lista de argumentos. El argumento *argv*[**n** + 1] debe ser un puntero **nulo** para marcar el final de la lista de argumentos.

*envp*<br/>
Matriz de punteros a la configuración del entorno

## <a name="return-value"></a>Valor devuelto

El valor devuelto de una **_spawnvpe** o **_wspawnvpe** sincrónica ( **_P_WAIT** especificado para el *modo*) es el estado de salida del nuevo proceso. El valor devuelto de una **_spawnvpe** o **_wspawnvpe** asincrónica ( **_P_NOWAIT** o **_P_NOWAITO** especificados para el *modo*) es el identificador del proceso. El estado de salida es 0 si el proceso finalizó normalmente. Puede establecer el estado de salida en un valor distinto de cero si el proceso generado llama específicamente a la rutina de **salida** con un argumento distinto de cero. Si el nuevo proceso no estableció explícitamente un estado de salida positivo, un estado de salida positivo indica un resultado anormal con una anulación o una interrupción. Un valor devuelto de-1 indica un error (el nuevo proceso no se inicia). En este caso, **errno** se establece en uno de los valores siguientes:

|||
|-|-|
| **E2BIG** | La lista de argumentos supera los 1024 bytes. |
| **EINVAL** | el argumento del *modo* no es válido. |
| **ENOENT** | El archivo o la ruta de acceso no se encuentra. |
| **ENOEXEC** | El archivo especificado no es ejecutable o no tiene un formato de archivo ejecutable válido. |
| **ENOMEM** | Memoria insuficiente para ejecutar el nuevo proceso. |

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

Cada una de estas funciones crea y ejecuta un proceso nuevo, pasando una matriz de punteros a los argumentos de la línea de comandos y una matriz de punteros a la configuración del entorno. Estas funciones usan la variable de entorno **path** para buscar el archivo que se va a ejecutar.

Estas funciones validan sus parámetros. Si *cmdname* o *argv* es un puntero nulo, o si *argv* apunta a un puntero nulo, o *argv*[0] es una cadena vacía, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL**y devuelven-1. No se genera ningún proceso nuevo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_spawnvpe**|\<stdio.h> o \<process.h>|
|**_wspawnvpe**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [_spawn, _wspawn (Funciones)](../../c-runtime-library/spawn-wspawn-functions.md).

## <a name="see-also"></a>Consulte también

[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
