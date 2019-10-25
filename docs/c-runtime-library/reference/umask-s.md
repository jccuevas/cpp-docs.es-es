---
title: _umask_s
ms.date: 11/04/2016
api_name:
- _umask_s
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: 21d9ba194f85e40c3c5a4d67d16ebca9721f68f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945982"
---
# <a name="_umask_s"></a>_umask_s

Establece la máscara de permisos de archivo predeterminados. Versión de [_umask](umask.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parámetros

*mode*<br/>
Configuración de permisos predeterminada.

*pOldMode*<br/>
Valor anterior de la configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Devuelve un código de error si el *modo* no especifica un modo válido o el puntero *pOldMode* es **null**.

### <a name="error-conditions"></a>Condiciones de error

|*mode*|*pOldMode*|Valor devuelto|Contenido de *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|any|**NULL**|**EINVAL**|no modificado|
|modo no válido|any|**EINVAL**|no modificado|

Si se da una de las condiciones anteriores, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_umask_s** devuelve **EINVAL** y establece **errno** en **EINVAL**.

## <a name="remarks"></a>Comentarios

La función **_umask_s** establece la máscara de permisos de archivo del proceso actual en el modo especificado por el *modo*. La máscara de permisos de archivo modifica la configuración de permisos de los nuevos archivos creados por **_creat**, _ **Open**o **_sopen**. Si un bit de la máscara es 1, el bit correspondiente del valor de permiso solicitado del archivo se establece en 0 (no permitido). Si un bit de la máscara es 0, el bit correspondiente se deja sin modificar. La configuración de permisos de un nuevo archivo no se establece hasta que se cierra el archivo por primera vez.

La expresión de entero *PMODE* contiene una o las dos constantes de manifiesto siguientes, definidas en SYS\STAT. C

|*pmode*||
|-|-|
|**_S_IWRITE**|Escritura permitida.|
|**_S_IREAD**|Lectura permitida.|
|**_S_IREAD** \| **_S_IWRITE**|Lectura y escritura permitidas.|

Cuando se proporcionan ambas constantes, se combinan con el operador bit a bit OR ( **|** ). Si el argumento de *modo* es **_S_IREAD**, no se permite la lectura (el archivo es de solo escritura). Si el argumento de *modo* es **_S_IWRITE**, no se permite la escritura (el archivo es de solo lectura). Por ejemplo, si el bit de escritura está establecido en la máscara, los nuevos archivos serán de solo lectura. Tenga en cuenta que en los sistemas operativos MS-DOS y Windows, todos los archivos se pueden leer; no se puede conceder permiso de solo escritura. Por lo tanto, establecer el bit de lectura con **_umask_s** no tiene ningún efecto en los modos del archivo.

Si *PMODE* no es una combinación de una de las constantes del manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente las omitirá.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_umask_s**|\<io.h>, \<sys/stat.h> y \<sys/types.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
