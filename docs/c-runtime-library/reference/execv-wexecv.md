---
title: _execv, _wexecv
ms.date: 4/2/2020
api_name:
- _wexecv
- _execv
- _o__execv
- _o__wexecv
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _execv
- _wexecv
- wexecv
helpviewer_keywords:
- _wexecv function
- _execv function
- wexecv function
- execv function
ms.assetid: 8dbaf7bc-9040-4316-a0c1-db7e866b52af
ms.openlocfilehash: 638364afa75fa1b04b598370473dee48964c5763
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347888"
---
# <a name="_execv-_wexecv"></a>_execv, _wexecv

Carga y ejecuta nuevos procesos secundarios.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _execv(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecv(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>Parámetros

*cmdname*<br/>
Ruta de acceso del archivo que se va a ejecutar.

*Argv*<br/>
Matriz de punteros a parámetros.

## <a name="return-value"></a>Valor devuelto

Si se ejecutan correctamente, estas funciones no vuelven al proceso de llamada. Un valor devuelto de -1 indica un error, en cuyo caso se establece la variable global **errno.**

|valor **errno**|Descripción|
|-------------------|-----------------|
|**E2BIG**|El espacio necesario para los argumentos y la configuración de entorno supera los 32 kB.|
|**EACCES**|El archivo especificado tiene un bloqueo o una infracción de uso compartido.|
|**EINVAL**|Parámetro no válido.|
|**EMFILE**|Hay demasiados archivos abiertos (se debe abrir el archivo especificado para determinar si es ejecutable).|
|**ENOENT**|No se encuentra el archivo o la ruta de acceso.|
|**ENOEXEC**|El archivo especificado no es ejecutable o tiene un formato de archivo ejecutable no válido.|
|**ENOMEM**|Memoria insuficiente para ejecutar el nuevo proceso; la memoria disponible se ha dañado; o existe un bloque no válido, lo que indica que el proceso de llamada no se asignó correctamente.|

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Cada una de estas funciones carga y ejecuta un proceso nuevo, y pasa una matriz de punteros a los argumentos de la línea de comandos.

Las funciones **_execv** validan sus parámetros. Si *cmdname* es un puntero nulo, o si *argv* es un puntero nulo, puntero a una matriz vacía o si la matriz contiene una cadena vacía como primer argumento, las **funciones _execv** invocan el controlador de parámetros no válidos como se describe en Validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno en** **EINVAL** y devuelven -1. No se inicia ningún proceso.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_execv**|\<process.h>|\<errno.h>|
|**_wexecv**|\<process.h> o \<wchar.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [Funciones _exec y _wexec](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funciones](../../c-runtime-library/exec-wexec-functions.md)<br/>
[Aborta](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, funciones _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
