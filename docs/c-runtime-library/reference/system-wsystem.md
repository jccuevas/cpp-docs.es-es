---
title: system, _wsystem
ms.date: 4/2/2020
api_name:
- system
- _wsystem
- _o__wsystem
- _o_system
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tsystem
- _wsystem
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
ms.openlocfilehash: 21ce04d30da80a40a1162dce06ff378150008766
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362790"
---
# <a name="system-_wsystem"></a>system, _wsystem

Ejecuta un comando.

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int system(
   const char *command
);
int _wsystem(
   const wchar_t *command
);
```

### <a name="parameters"></a>Parámetros

*Comando*<br/>
Comando que se va a ejecutar.

## <a name="return-value"></a>Valor devuelto

Si *el comando* es **NULL** y se encuentra el intérprete de comandos, devuelve un valor distinto de cero. Si no se encuentra el intérprete de comandos, devuelve 0 y establece **errno** en **ENOENT**. Si *el comando* no es **NULL**, el **sistema** devuelve el valor devuelto por el intérprete de comandos. Devuelve el valor 0 únicamente si el intérprete de comandos devuelve el valor 0. Un valor devuelto de - 1 indica un error y **errno** se establece en uno de los siguientes valores:

|||
|-|-|
| **E2BIG** | La lista de argumentos (que es dependiente del sistema) es demasiado grande. |
| **ENOENT** | No se encuentra el intérprete de comandos. |
| **ENOEXEC** | El archivo de intérprete de comandos no se puede ejecutar porque el formato no es válido. |
| **ENOMEM** | No hay suficiente memoria disponible para ejecutar el comando, la memoria disponible se ha dañado o existe un bloque no válido que indica que el proceso que realiza la llamada no se asignó correctamente. |

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de retorno.

## <a name="remarks"></a>Observaciones

La función del **sistema** pasa el *comando* al intérprete de comandos, que ejecuta la cadena como un comando del sistema operativo. **utiliza** las variables de entorno **COMSPEC** y **PATH** para localizar el archivo de intérprete de comandos CMD.exe. Si *el comando* es **NULL**, la función solo comprueba si existe el intérprete de comandos.

Debe vaciar explícitamente, utilizando [fflush](fflush.md) o [_flushall](flushall.md), o cerrar cualquier secuencia antes de llamar al **sistema**.

**_wsystem** es una versión de caracteres anchos del **sistema;** el argumento *de comando* para **_wsystem** es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**sistema**|**sistema**|**_wsystem**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**sistema**|\<process.h> o \<stdlib.h>|
|**_wsystem**|\<process.h> o \<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

En este ejemplo se utiliza **el sistema** para TYPE un archivo de texto.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crt_systemtxt"></a>Entrada: crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec funciones](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, funciones _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
