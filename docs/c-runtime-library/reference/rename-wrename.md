---
title: rename, _wrename
ms.date: 4/2/2020
api_name:
- rename
- _wrename
- _o__wrename
- _o_rename
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
- _wrename
- _trename
- Rename
helpviewer_keywords:
- trename function
- directories [C++], renaming
- renaming directories
- names [C++], changing file
- _trename function
- rename function
- wrename function
- files [C++], renaming
- _wrename function
- names [C++], changing directory
- renaming files
ms.assetid: 9f0a6103-26a2-4dda-b14b-79a48946266a
ms.openlocfilehash: b0a5f43d92d6dd85626f00bf5c2a6350e5bfa10f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917802"
---
# <a name="rename-_wrename"></a>rename, _wrename

Cambia el nombre de un archivo o de un directorio.

## <a name="syntax"></a>Sintaxis

```C
int rename(
   const char *oldname,
   const char *newname
);
int _wrename(
   const wchar_t *oldname,
   const wchar_t *newname
);
```

### <a name="parameters"></a>Parámetros

*oldname*<br/>
Puntero al nombre anterior.

*newname*<br/>
Puntero al nombre nuevo.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve 0 si se realiza correctamente. En un error, la función devuelve un valor distinto de cero y establece **errno** en uno de los valores siguientes:

|valor de errno|Condición|
|-|-|
| **EACCES** | El archivo o directorio especificado por *newname* ya existe o no se pudo crear (ruta de acceso no válida), o bien *oldname* es un directorio y *newname* especifica otra ruta de acceso. |
| **ENOENT** | Archivo o ruta de acceso especificado por *oldname* no encontrado. |
| **EINVAL** | El nombre contiene caracteres no válidos. |

Para otros valores devueltos posibles, vea [_doserrno, _errno, syserrlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **rename** cambia el nombre del archivo o directorio especificado por *oldname* por el nombre proporcionado por *newname*. El nombre anterior debe ser la ruta de acceso de un archivo o directorio existente. El nombre nuevo no debe ser el nombre de un archivo o directorio existente. Puede usar **rename** para mover un archivo de un directorio o dispositivo a otro indicando una ruta de acceso diferente en el argumento *newname*. Sin embargo, no puede usar **rename** para mover un directorio. Se puede cambiar el nombre de los directorios, pero estos no se pueden mover.

**_wrename** es una versión con caracteres anchos de **_rename**; los argumentos para **_wrename** son cadenas de caracteres anchos. **_wrename** y **_rename** se comportan de manera idéntica.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**rename**|**rename**|**_wrename**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**rename**|\<io.h> o \<stdio.h>|
|**_wrename**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_renamer.c
/* This program attempts to rename a file named
* CRT_RENAMER.OBJ to CRT_RENAMER.JBO. For this operation
* to succeed, a file named CRT_RENAMER.OBJ must exist and
* a file named CRT_RENAMER.JBO must not exist.
*/

#include <stdio.h>

int main( void )
{
   int  result;
   char old[] = "CRT_RENAMER.OBJ", new[] = "CRT_RENAMER.JBO";

   /* Attempt to rename file: */
   result = rename( old, new );
   if( result != 0 )
      printf( "Could not rename '%s'\n", old );
   else
      printf( "File '%s' renamed to '%s'\n", old, new );
}
```

### <a name="output"></a>Salida

```Output
File 'CRT_RENAMER.OBJ' renamed to 'CRT_RENAMER.JBO'
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
