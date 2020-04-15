---
title: _getcwd, _wgetcwd
description: C Las funciones de la biblioteca en tiempo de ejecución _getcwd, _wgetcwd obtener el directorio de trabajo actual.
ms.date: 4/2/2020
api_name:
- _wgetcwd
- _getcwd
- _o__getcwd
- _o__wgetcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _getcwd
- wgetcwd
- _wgetcwd
- tgetcwd
- _tgetcwd
helpviewer_keywords:
- getcwd function
- working directory
- _wgetcwd function
- _getcwd function
- current working directory
- wgetcwd function
- directories [C++], current working
ms.assetid: 888dc8c6-5595-4071-be55-816b38e3e739
ms.openlocfilehash: bc19a416ebebeb901e8dbb435971e6d5f33e4067
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344441"
---
# <a name="_getcwd-_wgetcwd"></a>_getcwd, _wgetcwd

Obtiene el directorio de trabajo actual.

## <a name="syntax"></a>Sintaxis

```C
char *_getcwd(
   char *buffer,
   int maxlen
);
wchar_t *_wgetcwd(
   wchar_t *buffer,
   int maxlen
);
```

### <a name="parameters"></a>Parámetros

*Búfer*\
Ubicación de almacenamiento de la ruta de acceso.

*maxlen*\
Longitud máxima de la ruta de acceso en caracteres: **char** para **_getcwd** y **wchar_t** para **_wgetcwd**.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero al *búfer*. Un valor devuelto **NULL** indica un error y **errno** se establece en **ENOMEM**, lo que indica que no hay memoria suficiente para asignar bytes *maxlen* (cuando se proporciona un argumento **NULL** como *búfer),* o en **ERANGE**, lo que indica que la ruta de acceso es más larga que los caracteres *maxlen.* Si *maxlen* es menor o igual que cero, esta función invoca un controlador de parámetros no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_getcwd** obtiene la ruta de acceso completa del directorio de trabajo actual para la unidad predeterminada y la almacena en el *búfer.* El argumento entero *maxlen* especifica la longitud máxima de la ruta de acceso. Se produce un error si la longitud de la ruta de acceso (incluido el carácter nulo de terminación) supera *maxlen*. El argumento *buffer* puede ser **NULL**; un búfer de al menos tamaño *maxlen* (más solo si es necesario) se asigna automáticamente, utilizando **malloc,** para almacenar la ruta. Este búfer se puede liberar más adelante llamando a **free** y pasándole el **valor devuelto _getcwd** (un puntero al búfer asignado).

**_getcwd** devuelve una cadena que representa la ruta de acceso del directorio de trabajo actual. Si el directorio de trabajo actual es la raíz, la cadena termina con una barra diagonal inversa (`\`). Si el directorio de trabajo actual es un directorio distinto de la raíz, la cadena finaliza con el nombre de directorio y no con una barra diagonal inversa.

**_wgetcwd** es una versión de caracteres anchos de **_getcwd;** el argumento *de búfer* y el valor devuelto de **_wgetcwd** son cadenas de caracteres anchos. **_wgetcwd** y **_getcwd** comportarse de forma idéntica de lo contrario.

Cuando se definen **_DEBUG** y **_CRTDBG_MAP_ALLOC,** las llamadas a **_getcwd** y **_wgetcwd** se reemplazan por llamadas a **_getcwd_dbg** y **_wgetcwd_dbg** para permitir la depuración de asignaciones de memoria. Para obtener más información, vea [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_getcwd.c
// Compile with: cl /W4 crt_getcwd.c
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h> // _getcwd
#include <stdlib.h> // free, perror
#include <stdio.h>  // printf
#include <string.h> // strlen

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if ( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %zu\n", buffer, strlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Consulte también

[Control de directorios](../../c-runtime-library/directory-control.md)\
[_chdir, _wchdir](chdir-wchdir.md)\
[_mkdir, _wmkdir](mkdir-wmkdir.md)\
[_rmdir, _wrmdir](rmdir-wrmdir.md)
