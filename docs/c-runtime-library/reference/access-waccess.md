---
title: _access, _waccess
ms.date: 4/2/2020
api_name:
- _access
- _waccess
- _o__access
- _o__waccess
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: ae213768e30fa8120a80aaa30b3fe1b53e802d78
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920268"
---
# <a name="_access-_waccess"></a>_access, _waccess

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

Cada función devuelve 0 si el archivo tiene el modo especificado. La función devuelve-1 si el archivo con nombre no existe o no tiene el modo especificado; en este caso, `errno` se establece tal y como se muestra en la tabla siguiente.

|||
|-|-|
`EACCES`|Acceso denegado: la configuración de permisos del archivo no permite el acceso especificado.
`ENOENT`|No se encuentra el nombre o la ruta de acceso del archivo.
`EINVAL`|Parámetro no válido.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Cuando se usa con archivos, la función **_access** determina si existe el archivo o directorio especificado y tiene los atributos especificados por el valor de *mode*. Cuando se usa con directorios, **_access** solo determina si existe el directorio especificado; en Windows 2000 y sistemas operativos posteriores, todos los directorios tienen acceso de lectura y escritura.

|valor de *modo*|Comprueba el archivo para|
|------------------|---------------------|
|00|Solo existencia|
|02|Solo escritura|
|04|De sólo lectura|
|06|Operaciones de lectura y escritura|

Esta función solo comprueba si el archivo y directorio son de solo lectura o no; no comprueba la configuración de seguridad del sistema de archivos. Para eso necesita un token de acceso. Para obtener más información sobre la seguridad del sistema de archivos, consulte [Tokens de acceso](/windows/win32/SecAuthZ/access-tokens). Existe una clase ATL que proporciona esta funcionalidad; consulte [Clase CAccessToken](../../atl/reference/caccesstoken-class.md).

**_waccess** es una versión con caracteres anchos de **_access**; el argumento de *ruta de acceso* para **_waccess** es una cadena de caracteres anchos. **_waccess** y **_access** se comportan de manera idéntica.

Esta función valida sus parámetros. Si *path* es null o el *modo* no especifica un modo válido, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve -1.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

## <a name="see-also"></a>Consulta también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)
