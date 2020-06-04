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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b1bc89ce51fff44a847111d68cac8e8b3f58a635
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917009"
---
# <a name="_chmod-_wchmod"></a>_chmod, _wchmod

Cambia la configuración de permisos de archivo.

## <a name="syntax"></a>Sintaxis

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>Parámetros

*extensión*<br/>
Nombre del archivo existente.

*pmode*<br/>
Configuración de permisos del archivo.

## <a name="return-value"></a>Valor devuelto

Estas funciones devuelven 0 si la configuración de permisos se ha modificado correctamente. Un valor devuelto de-1 indica un error. Si no se encuentra el archivo especificado, **errno** se establece en **ENOENT**; Si un parámetro no es válido, **errno** se establece en **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **_chmod** cambia la configuración de permisos del archivo especificado por *filename*. La configuración de permisos controla el acceso de lectura y escritura al archivo. La expresión de entero *PMODE* contiene una o las dos constantes de manifiesto siguientes, definidas en SYS\Stat.h.

| *pmode* | Significado |
|-|-|
| **\_S\_iRead** | Solo se permite la lectura. |
| **\_S\_IWRITE** | Escritura permitida. (De hecho, se permiten la lectura y escritura). |
| **\_S\_iRead** &#124; ** \_s\_IWRITE** | Lectura y escritura permitidas. |

Cuando se proporcionan ambas constantes, se unen con el operador bit a bit or (**\|**). Si no se ha concedido el permiso de escritura, el archivo será de solo lectura. Tenga en cuenta que todos los archivos son siempre legibles; es decir, no es posible conceder permisos de solo escritura. Por lo tanto, los modos **_S_IWRITE** y **_S_IREAD** \| **_S_IWRITE** son equivalentes.

**_wchmod** es una versión con caracteres anchos de **_chmod**; el argumento *filename* para **_wchmod** es una cadena de caracteres anchos. **_wchmod** y **_chmod** se comportan de manera idéntica.

Esta función valida sus parámetros. Si *PMODE* no es una combinación de una de las constantes del manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente las omite. Si *filename* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve-1.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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
