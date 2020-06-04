---
title: _umask
ms.date: 4/2/2020
api_name:
- _umask
- _o__umask
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
- _umask
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
ms.openlocfilehash: 84735374a936e47691df82247f0202ecfcd86d9d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913842"
---
# <a name="_umask"></a>_umask

Establece la máscara de permisos de archivo predeterminados. Hay disponible una versión más segura de esta función; vea [_umask_s](umask-s.md).

## <a name="syntax"></a>Sintaxis

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parámetros

*pmode*<br/>
Configuración de permisos predeterminada.

## <a name="return-value"></a>Valor devuelto

**_umask** devuelve el valor anterior de *PMODE*. No se devuelve ningún error.

## <a name="remarks"></a>Observaciones

La función **_umask** establece la máscara de permisos de archivo del proceso actual en el modo especificado por *PMODE*. La máscara de permisos de archivo modifica la configuración de permisos de los nuevos archivos creados por **_creat**, **_open**o **_sopen**. Si un bit de la máscara es 1, el bit correspondiente del valor de permiso solicitado del archivo se establece en 0 (no permitido). Si un bit de la máscara es 0, el bit correspondiente se deja sin modificar. La configuración de permisos de un nuevo archivo no se establece hasta que se cierra el archivo por primera vez.

La expresión de entero *PMODE* contiene una o las dos constantes de manifiesto siguientes, definidas en SYS\STAT. C

|*pmode*| |
|-|-|
| **_S_IWRITE** | Escritura permitida. |
| **_S_IREAD** | Lectura permitida. |
| **_S_IREAD** &#124; **_S_IWRITE** | Lectura y escritura permitidas. |

Cuando se proporcionan ambas constantes, se combinan con el operador OR bit a bit ( **&#124;** ). Si el argumento *PMODE* es **_S_IREAD**, no se permite la lectura (el archivo es de solo escritura). Si el argumento *PMODE* es **_S_IWRITE**, no se permite la escritura (el archivo es de solo lectura). Por ejemplo, si el bit de escritura está establecido en la máscara, los nuevos archivos serán de solo lectura. Tenga en cuenta que en los sistemas operativos MS-DOS y Windows, todos los archivos se pueden leer; no se puede conceder permiso de solo escritura. Por lo tanto, establecer el bit de lectura con **_umask** no tiene ningún efecto en los modos del archivo.

Si *PMODE* no es una combinación de una de las constantes del manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente las omitirá.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_umask.c
// compile with: /W3
// This program uses _umask to set
// the file-permission mask so that all future
// files will be created as read-only files.
// It also displays the old mask.
#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask;

   /* Create read-only files: */
   oldmask = _umask( _S_IWRITE ); // C4996
   // Note: _umask is deprecated; consider using _umask_s instead
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
