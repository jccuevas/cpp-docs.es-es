---
title: system, _wsystem | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- system
- _wsystem
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
- _tsystem
- _wsystem
dev_langs:
- C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9043b5bb76c438ee640f298eeed3f41b84a7ca30
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="system-wsystem"></a>system, _wsystem

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

*command*<br/>
Comando que se va a ejecutar.

## <a name="return-value"></a>Valor devuelto

Si *comando* es **NULL** y se encuentra el intérprete de comandos, devuelve un valor distinto de cero. Si no se encuentra el intérprete de comandos, devuelve 0 y establece **errno** a **ENOENT**. Si *comando* no **NULL**, **system** devuelve el valor devuelto por el intérprete de comandos. Devuelve el valor 0 únicamente si el intérprete de comandos devuelve el valor 0. Un valor devuelto de - 1 indica un error, y **errno** se establece en uno de los siguientes valores:

|||
|-|-|
**E2BIG**|La lista de argumentos (que es dependiente del sistema) es demasiado grande.
**ENOENT**|No se encuentra el intérprete de comandos.
**ENOEXEC**|El archivo de intérprete de comandos no se puede ejecutar porque el formato no es válido.
**ENOMEM**|No hay suficiente memoria disponible para ejecutar el comando, la memoria disponible se ha dañado o existe un bloque no válido que indica que el proceso que realiza la llamada no se asignó correctamente.

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos códigos de retorno.

## <a name="remarks"></a>Comentarios

El **system** función pasa *comando* al intérprete de comandos, que ejecuta la cadena como un comando del sistema operativo. **sistema** utiliza la **COMSPEC** y **ruta de acceso** variables de entorno para buscar el intérprete de comandos CMD.exe de archivos. Si *comando* es **NULL**, la función comprueba si existe el intérprete de comandos.

Debe vaciar explícitamente, mediante el uso de [fflush](fflush.md) o [_flushall](flushall.md), o cerrar todos los flujos antes de llamar a **system**.

**_wsystem** es una versión con caracteres anchos de **system**; el *comando* argumento pasado a **_wsystem** es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsystem**|**system**|**system**|**_wsystem**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**system**|\<process.h> o \<stdlib.h>|
|**_wsystem**|\<process.h> o \<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Este ejemplo se utiliza **system** para escribir un archivo de texto.

```C
// crt_system.c

#include <process.h>

int main( void )
{
   system( "type crt_system.txt" );
}
```

### <a name="input-crtsystemtxt"></a>Entrada: crt_system.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
