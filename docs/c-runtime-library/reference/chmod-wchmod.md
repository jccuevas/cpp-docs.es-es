---
title: _chmod, _wchmod
ms.date: 4/2/2020
api_name:
- _chmod
- _wchmod
- _o__chmod
- _o__wchmod
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _chmod
- _wchmod
- wchmod
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
ms.openlocfilehash: faceb49c921162da042f863abbebbe2ef0a52153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350095"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

Cambia la configuración de permisos de archivo.

## <a name="syntax"></a>Sintaxis

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parámetros

*Nombre*<br/>
Nombre del archivo existente.

*pmode*<br/>
Configuración de permisos del archivo.

## <a name="return-value"></a>Valor devuelto

Estas funciones devuelven 0 si la configuración de permisos se ha modificado correctamente. Un valor devuelto de -1 indica un error. Si no se pudo encontrar el archivo especificado, **errno** se establece **en ENOENT**; si un parámetro no es válido, **errno** se establece **en EINVAL**.

## <a name="remarks"></a>Observaciones

La función **_chmod** cambia la configuración de permisos del archivo especificado por *filename*. La configuración de permisos controla el acceso de lectura y escritura al archivo. La expresión de entero *pmode* contiene una o ambas de las siguientes constantes de manifiesto, definidas en SYS-Stat.h.

| *pmode* | Significado |
|-|-|
| **\_S\_IREAD** | Solo se permite la lectura. |
| **\_S\_IWRITE** | Escritura permitida. (De hecho, se permiten la lectura y escritura). |
| **\_S\_IREAD** &#124; ** \_\_S IWRITE** | Lectura y escritura permitidas. |

Cuando se dan ambas constantes, se unen**\|** con el operador o bit a bit ( ). Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. Tenga en cuenta que todos los archivos son siempre legibles; es decir, no es posible conceder permisos de solo escritura. Por lo tanto, los modos **_S_IWRITE** y **_S_IREAD** \| **_S_IWRITE** son equivalentes.

**_wchmod** es una versión de caracteres anchos de **_chmod;** el argumento *filename* que **se va** a _wchmod es una cadena de caracteres anchos. **_wchmod** y **_chmod** comportarse de forma idéntica de lo contrario.

Esta función valida sus parámetros. Si *pmode* no es una combinación de una de las constantes de manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente las ignora. Si *filename* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece **en EINVAL** y la función devuelve -1.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wchmod**|\<io.h> o \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.
```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_access, _waccess](access-waccess.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_fstat, _fstat32, _fstat64, _fstati64, _fstat32i64, _fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_stat, _wstat (Funciones)](stat-functions.md)<br/>
