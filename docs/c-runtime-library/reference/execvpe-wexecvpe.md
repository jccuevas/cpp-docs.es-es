---
title: _execvpe, _wexecvpe
ms.date: 4/2/2020
api_name:
- _execvpe
- _wexecvpe
- _o__execvpe
- _o__wexecvpe
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wexecvpe
- _wexecvpe
- _execvpe
helpviewer_keywords:
- wexecvpe function
- execvpe function
- _wexecvpe function
- _execvpe function
ms.assetid: c0c3c986-d9c0-4814-a96c-10f0b3092766
ms.openlocfilehash: 4a1a2d66600a7502c088577adca4085c68e4ccd7
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909704"
---
# <a name="_execvpe-_wexecvpe"></a>_execvpe, _wexecvpe

Carga y ejecuta nuevos procesos secundarios.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
intptr_t _execvpe(
   const char *cmdname,
   const char *const *argv,
   const char *const *envp
);
intptr_t _wexecvpe(
   const wchar_t *cmdname,
   const wchar_t *const *argv,
   const wchar_t *const *envp
);
```

### <a name="parameters"></a>Parámetros

*cmdname*<br/>
Ruta de acceso del archivo que se va a ejecutar.

*argv*<br/>
Matriz de punteros a parámetros.

*envp*<br/>
Matriz de punteros a la configuración del entorno.

## <a name="return-value"></a>Valor devuelto

Si se ejecutan correctamente, estas funciones no vuelven al proceso de llamada. Un valor devuelto de-1 indica un error, en cuyo caso se establece la variable global **errno** .

|valor **errno**|Descripción|
|-------------------|-----------------|
|**E2BIG**|El espacio necesario para los argumentos y la configuración de entorno supera los 32 KB.|
|**EACCES**|El archivo especificado tiene un bloqueo o una infracción de uso compartido.|
|**EMFILE**|Hay demasiados archivos abiertos. (Se debe abrir el archivo especificado para determinar si es ejecutable).|
|**ENOENT**|No se encuentra el archivo o la ruta de acceso.|
|**ENOEXEC**|El archivo especificado no es ejecutable o tiene un formato de archivo ejecutable no válido.|
|**ENOMEM**|No hay memoria suficiente para ejecutar el nuevo proceso; la memoria disponible se ha dañado o existe un bloque no válido que indica que el proceso de llamada no se asignó correctamente.|

Para más información sobre estos y otros códigos devueltos, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Cada una de estas funciones carga y ejecuta un proceso nuevo, pasando una matriz de punteros a los argumentos de la línea de comandos y una matriz de punteros a la configuración del entorno. Estas funciones usan la variable de entorno **path** para buscar el archivo que se va a ejecutar.

Las funciones **_execvpe** validan sus parámetros. Si *cmdname* es un puntero nulo, o si *argv* es un puntero nulo, un puntero a una matriz vacía o un puntero a una matriz que contiene una cadena vacía como primer argumento, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven-1. No se inicia ningún proceso.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezado opcional|
|--------------|---------------------|---------------------|
|**_execvpe**|\<process.h>|\<errno.h>|
|**_wexecvpe**|\<process.h> o \<wchar.h>|\<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Consulte el ejemplo de [Funciones _exec y _wexec](../../c-runtime-library/exec-wexec-functions.md).

## <a name="see-also"></a>Consulta también

[Control de proceso y entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funciones](../../c-runtime-library/exec-wexec-functions.md)<br/>
[aborta](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn funciones](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
