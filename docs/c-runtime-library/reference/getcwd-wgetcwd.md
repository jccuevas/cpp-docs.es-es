---
title: _getcwd, _wgetcwd
description: Funciones de la biblioteca en tiempo de ejecución de C _getcwd, _wgetcwd obtener el directorio de trabajo actual.
ms.date: 09/24/2019
api_name:
- _wgetcwd
- _getcwd
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
ms.openlocfilehash: 27cfdc1eb59c2de788bbe5963a6fccffcb62cba0
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274625"
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

*búfer*\
Ubicación de almacenamiento de la ruta de acceso.

*Maxlen*\
Longitud máxima de la ruta de acceso en caracteres: **Char** para **_getcwd** y **wchar_t** para **_wgetcwd**.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero al *búfer*. Un valor devuelto **null** indica un error y **errno** se establece en **ENOMEM**, lo que indica que no hay memoria suficiente para asignar *Maxlen* bytes (cuando se proporciona un argumento **null** como *buffer*) o a **ERANGE** , que indica que la ruta de acceso tiene más de *Maxlen* caracteres. Si *Maxlen* es menor o igual que cero, esta función invoca un controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_getcwd** obtiene la ruta de acceso completa del directorio de trabajo actual para la unidad predeterminada y la almacena en el *búfer*. El argumento de entero *Maxlen* especifica la longitud máxima de la ruta de acceso. Se produce un error si la longitud de la ruta de acceso (incluido el carácter nulo de terminación) supera el valor de *Maxlen*. El argumento de *búfer* puede ser **null**; se asigna automáticamente un búfer de al menos el tamaño *Maxlen* (más solo si es necesario), mediante **malloc**, para almacenar la ruta de acceso. Este búfer se puede liberar más adelante llamando a **Free** y pasándole el valor devuelto de **_getcwd** (un puntero al búfer asignado).

**_getcwd** devuelve una cadena que representa la ruta de acceso del directorio de trabajo actual. Si el directorio de trabajo actual es la raíz, la cadena finaliza con una barra diagonal`\`inversa (). Si el directorio de trabajo actual es un directorio distinto de la raíz, la cadena finaliza con el nombre de directorio y no con una barra diagonal inversa.

**_wgetcwd** es una versión con caracteres anchos de **_getcwd**; el argumento de *búfer* y el valor devuelto de **_wgetcwd** son cadenas de caracteres anchos. **_wgetcwd** y **_getcwd** se comportan de manera idéntica.

Cuando se definen **_ Debug y _** **crtdbg_map_alloc** , las llamadas a **_getcwd** y **_wgetcwd** se reemplazan por llamadas a **_getcwd_dbg** y **_wgetcwd_dbg** para permitir la depuración de asignaciones de memoria. Para obtener más información, vea [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tgetcwd**|**_getcwd**|**_getcwd**|**_wgetcwd**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getcwd**|\<direct.h>|
|**_wgetcwd**|\<direct.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Control de directorio](../../c-runtime-library/directory-control.md)\
[_chdir, _wchdir](chdir-wchdir.md)\
[_mkdir, _wmkdir](mkdir-wmkdir.md)\
[_rmdir, _wrmdir](rmdir-wrmdir.md)
