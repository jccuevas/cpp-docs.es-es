---
title: rename, _wrename
ms.date: 11/04/2016
apiname:
- rename
- _wrename
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
ms.openlocfilehash: 3536bfb6c38c99a8d6d943102fb9303dd4d85b7b
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326145"
---
# <a name="rename-wrename"></a>rename, _wrename

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

Cada una de estas funciones devuelve 0 si se realiza correctamente. Produce un error, la función devuelve un valor distinto de cero y establece **errno** a uno de los siguientes valores:

|valor de errno|Condición|
|-|-|
| **EACCES** | El archivo o directorio especificado por *newname* ya existe o no se pudo crear (ruta de acceso no válida), o bien *oldname* es un directorio y *newname* especifica otra ruta de acceso. |
| **ENOENT** | Archivo o ruta de acceso especificado por *oldname* no encontrado. |
| **EINVAL** | El nombre contiene caracteres no válidos. |

Para otros valores devueltos posibles, vea [_doserrno, _errno, syserrlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **rename** cambia el nombre del archivo o directorio especificado por *oldname* por el nombre proporcionado por *newname*. El nombre anterior debe ser la ruta de acceso de un archivo o directorio existente. El nombre nuevo no debe ser el nombre de un archivo o directorio existente. Puede usar **rename** para mover un archivo de un directorio o dispositivo a otro indicando una ruta de acceso diferente en el argumento *newname*. Sin embargo, no puede usar **rename** para mover un directorio. Se puede cambiar el nombre de los directorios, pero estos no se pueden mover.

**_wrename** es una versión con caracteres anchos de **_rename**; los argumentos de **_wrename** son cadenas de caracteres anchos. **_wrename** y **_rename** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_trename**|**rename**|**rename**|**_wrename**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**rename**|\<io.h> o \<stdio.h>|
|**_wrename**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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
