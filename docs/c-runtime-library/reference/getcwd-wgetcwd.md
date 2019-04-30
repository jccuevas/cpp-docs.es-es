---
title: _getcwd, _wgetcwd
ms.date: 11/04/2016
apiname:
- _wgetcwd
- _getcwd
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: 4c533f0e716cb9a13c152b9be3c46f60291118d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331797"
---
# <a name="getcwd-wgetcwd"></a>_getcwd, _wgetcwd

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

*buffer*<br/>
Ubicación de almacenamiento de la ruta de acceso.

*maxlen*<br/>
Longitud máxima de la ruta de acceso en caracteres: **char** para **_getcwd** y **wchar_t** para **_wgetcwd**.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero a *búfer*. Un **NULL** valor devuelto indica un error, y **errno** se establece en **ENOMEM**, que indica que no hay memoria suficiente para asignar *maxlen* bytes (cuando un **NULL** argumento se asigna como *búfer*), o a **ERANGE**, que indica que la ruta de acceso es mayor que *maxlen*  caracteres. Si *maxlen* es menor o igual a cero, esta función invoca un controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_getcwd** función obtiene la ruta de acceso completa del directorio de trabajo actual para la unidad predeterminada y lo almacena en *búfer*. El argumento de entero *maxlen* especifica la longitud máxima de la ruta de acceso. Se produce un error si se supera la longitud de la ruta de acceso (incluido el carácter nulo final) *maxlen*. El *búfer* argumento puede ser **NULL**; un búfer de tamaño mínimo *maxlen* (más solo en caso necesario) se asigna automáticamente mediante **malloc**, para almacenar la ruta de acceso. Más adelante se puede liberar este búfer mediante una llamada a **libre** y pasándole el **_getcwd** devolver valor (un puntero al búfer asignado).

**_getcwd** devuelve una cadena que representa la ruta de acceso del directorio de trabajo actual. Si el directorio de trabajo actual es la raíz, la cadena finaliza con una barra diagonal inversa ( **\\** ). Si el directorio de trabajo actual es un directorio distinto de la raíz, la cadena finaliza con el nombre de directorio y no con una barra diagonal inversa.

**_wgetcwd** es una versión con caracteres anchos de **_getcwd**; el *búfer* argumento y el valor devuelto de **_wgetcwd** son cadenas de caracteres anchos. **_wgetcwd** y **_getcwd** se comportan exactamente igual.

Cuando **_DEBUG** y **_CRTDBG_MAP_ALLOC** se definen, las llamadas a **_getcwd** y **_wgetcwd** se reemplazan por llamadas a **_ getcwd_dbg** y **_wgetcwd_dbg** para permitir que las asignaciones de memoria de depuración. Para obtener más información, vea [_getcwd_dbg, _wgetcwd_dbg](getcwd-dbg-wgetcwd-dbg.md).

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
// This program places the name of the current directory in the
// buffer array, then displays the name of the current directory
// on the screen. Passing NULL as the buffer forces getcwd to allocate
// memory for the path, which allows the code to support file paths
// longer than _MAX_PATH, which are supported by NTFS.

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char* buffer;

   // Get the current working directory:
   if( (buffer = _getcwd( NULL, 0 )) == NULL )
      perror( "_getcwd error" );
   else
   {
      printf( "%s \nLength: %d\n", buffer, strnlen(buffer) );
      free(buffer);
   }
}
```

```Output
C:\Code
```

## <a name="see-also"></a>Vea también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
