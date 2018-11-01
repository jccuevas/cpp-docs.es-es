---
title: _access, _waccess
ms.date: 11/04/2016
apiname:
- _access
- _waccess
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _waccess
- _access
- taccess
- waccess
- _taccess
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
ms.openlocfilehash: 87ac912ab47483929b3afc2357331f8d97264b31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565482"
---
# <a name="access-waccess"></a>_access, _waccess

Determina si un archivo es de solo lectura o no. Hay disponibles versiones más seguras de estas funciones; consulte [_access_s, _waccess_s](access-s-waccess-s.md).

## <a name="syntax"></a>Sintaxis

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>Parámetros

*path*<br/>
Ruta de acceso del directorio o archivo.

*mode*<br/>
Atributo de lectura y escritura.

## <a name="return-value"></a>Valor devuelto

Cada función devuelve 0 si el archivo tiene el modo especificado. La función devuelve -1 si el archivo especificado no existe o no tiene el modo determinado; en este caso, `errno` se establece como se muestra en la tabla siguiente.

|||
|-|-|
`EACCES`|Acceso denegado: la configuración de permisos del archivo no permite el acceso especificado.
`ENOENT`|No se encuentra el nombre o la ruta de acceso del archivo.
`EINVAL`|Parámetro no válido.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cuando se usa con archivos, la **_access** función determina si el archivo o directorio especificado existe y tiene los atributos especificados por el valor de *modo*. Cuando se usa con directorios, **_access** solo determina si existe el directorio especificado; en Windows 2000 y versiones posteriores sistemas operativos, todos los directorios leído y acceso de escritura.

|*modo* valor|Comprueba el archivo para|
|------------------|---------------------|
|00|Solo existencia|
|02|Solo escritura|
|04|De sólo lectura|
|06|Operaciones de lectura y escritura|

Esta función solo comprueba si el archivo y directorio son de solo lectura o no; no comprueba la configuración de seguridad del sistema de archivos. Para eso necesita un token de acceso. Para obtener más información sobre la seguridad del sistema de archivos, consulte [Tokens de acceso](/windows/desktop/SecAuthZ/access-tokens). Existe una clase ATL que proporciona esta funcionalidad; consulte [Clase CAccessToken](../../atl/reference/caccesstoken-class.md).

**_waccess** es una versión con caracteres anchos de **_access**; el *ruta* argumento **_waccess** es una cadena de caracteres anchos. **_waccess** y **_access** se comportan exactamente igual.

Esta función valida sus parámetros. Si *ruta* es NULL o *modo* no especifica un modo válido, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve -1.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<wchar.h> o \<io.h>|\<errno.h>|

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se usa **_access** para comprobar el archivo denominado crt_ACCESS. C para ver si existe y si se permite la escritura.

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)