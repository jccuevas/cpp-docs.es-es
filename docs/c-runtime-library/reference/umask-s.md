---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
ms.openlocfilehash: d590910d5f5092a78ad64c8f9ef0aa259211e226
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362180"
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

*Modo*<br/>
Configuración de permisos predeterminada.

*pOldMode*<br/>
Valor anterior de la configuración de permisos.

## <a name="return-value"></a>Valor devuelto

Devuelve un código de error si *mode* no especifica un modo válido o el puntero *pOldMode* es **NULL**.

### <a name="error-conditions"></a>Condiciones de error

|*Modo*|*pOldMode*|Valor devuelto|Contenido de *pOldMode*|
|------------|----------------|----------------------|--------------------------------|
|cualquiera|**Null**|**EINVAL**|no modificado|
|modo no válido|cualquiera|**EINVAL**|no modificado|

Si se da una de las condiciones anteriores, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_umask_s** devuelve **EINVAL** y establece **errno** en **EINVAL**.

## <a name="remarks"></a>Observaciones

La función **_umask_s** establece la máscara de permiso de archivo del proceso actual en el modo especificado por *mode*. La máscara de permiso de archivo modifica la configuración de permisos de los nuevos archivos creados por **_creat**, **_open**o **_sopen**. Si un bit de la máscara es 1, el bit correspondiente del valor de permiso solicitado del archivo se establece en 0 (no permitido). Si un bit de la máscara es 0, el bit correspondiente se deja sin modificar. La configuración de permisos de un nuevo archivo no se establece hasta que se cierra el archivo por primera vez.

La expresión de enteros *pmode* contiene una o ambas de las siguientes constantes de manifiesto, definidas en SYS-STAT. H:

|*pmode*||
|-|-|
|**_S_IWRITE**|Escritura permitida.|
|**_S_IREAD**|Lectura permitida.|
|**_S_IREAD** \| **_S_IWRITE**|Lectura y escritura permitidas.|

Cuando se proporcionan ambas constantes, se unen con **|** el operador OR bit a bit ( ). Si el argumento *mode* es **_S_IREAD**, no se permite leer (el archivo es de solo escritura). Si el argumento *mode* es **_S_IWRITE**, no se permite escribir (el archivo es de solo lectura). Por ejemplo, si el bit de escritura está establecido en la máscara, los nuevos archivos serán de solo lectura. Tenga en cuenta que en los sistemas operativos MS-DOS y Windows, todos los archivos se pueden leer; no se puede conceder permiso de solo escritura. Por lo tanto, establecer el bit de lectura con **_umask_s** no tiene ningún efecto en los modos del archivo.

Si *pmode* no es una combinación de una de las constantes de manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente las ignorará.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_umask_s**|\<io.h>, \<sys/stat.h> y \<sys/types.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
