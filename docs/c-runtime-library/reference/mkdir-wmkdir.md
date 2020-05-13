---
title: _mkdir, _wmkdir
ms.date: 4/2/2020
api_name:
- _wmkdir
- _mkdir
- _o__mkdir
- _o__wmkdir
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
- _mkdir
- tmkdir
- _tmkdir
- wmkdir
- _wmkdir
helpviewer_keywords:
- _wmkdir function
- folders [C++], creating
- wmkdir function
- directories [C++], creating
- mkdir function
- tmkdir function
- _mkdir function
- _tmkdir function
ms.assetid: 7f22d01d-63a5-4712-a6e7-d34878b2d840
ms.openlocfilehash: f4714e3e763b827772a7d2eb61ae2e14f0aece02
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919148"
---
# <a name="_mkdir-_wmkdir"></a>_mkdir, _wmkdir

Crea un directorio nuevo.

## <a name="syntax"></a>Sintaxis

```C

int _mkdir(
   const char *dirname
);
int _wmkdir(
   const wchar_t *dirname
);
```

### <a name="parameters"></a>Parámetros

*dirname*<br/>
Ruta de acceso de un directorio nuevo.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el valor 0 si se ha creado el directorio nuevo. En un error, la función devuelve-1 y establece **errno** de la siguiente manera.

**EEXIST** No se creó el directorio porque *dirname* es el nombre de un archivo, directorio o dispositivo existente.

**ENOENT** No se encontró la ruta de acceso.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_mkdir** crea un nuevo directorio con el *dirname especificado.* **_mkdir** solo puede crear un nuevo directorio por llamada, por lo que solo el último componente de *dirname* puede asignar un nombre a un nuevo directorio. **_mkdir** no traduce los delimitadores de ruta de acceso. En Windows NT, la barra diagonal inversa (\\) y la barra diagonal (/) son delimitadores de ruta de acceso válidos para las cadenas de caracteres de las rutinas en tiempo de ejecución.

**_wmkdir** es una versión con caracteres anchos de **_mkdir**; el argumento *dirname* para **_wmkdir** es una cadena de caracteres anchos. **_wmkdir** y **_mkdir** se comportan de manera idéntica.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmkdir**|**_mkdir**|**_mkdir**|**_wmkdir**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_mkdir**|\<direct.h>|
|**_wmkdir**|\<direct.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_makedir.c

#include <direct.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   if( _mkdir( "\\testtmp" ) == 0 )
   {
      printf( "Directory '\\testtmp' was successfully created\n" );
      system( "dir \\testtmp" );
      if( _rmdir( "\\testtmp" ) == 0 )
        printf( "Directory '\\testtmp' was successfully removed\n"  );
      else
         printf( "Problem removing directory '\\testtmp'\n" );
   }
   else
      printf( "Problem creating directory '\\testtmp'\n" );
}
```

### <a name="sample-output"></a>Salida de ejemplo

```Output
Directory '\testtmp' was successfully created
Volume in drive C has no label.
Volume Serial Number is E078-087A

Directory of C:\testtmp

02/12/2002  09:56a      <DIR>          .
02/12/2002  09:56a      <DIR>          ..
               0 File(s)              0 bytes
               2 Dir(s)  15,498,690,560 bytes free
Directory '\testtmp' was successfully removed
```

## <a name="see-also"></a>Consulta también

[Control de directorio](../../c-runtime-library/directory-control.md)<br/>
[_chdir, _wchdir](chdir-wchdir.md)<br/>
[_rmdir, _wrmdir](rmdir-wrmdir.md)<br/>
