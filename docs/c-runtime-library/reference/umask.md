---
title: _umask | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _umask
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
- _umask
dev_langs:
- C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: beced2cbbd811f726433ed8ba7fd756c75ce46c0
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="umask"></a>_umask

Establece la máscara de permisos de archivo predeterminados. Hay disponible una versión más segura de esta función; vea [_umask_s](umask-s.md).

## <a name="syntax"></a>Sintaxis

```C
int _umask( int pmode );
```

### <a name="parameters"></a>Parámetros

*pmode*<br/>
Configuración de permisos predeterminada.

## <a name="return-value"></a>Valor devuelto

**_umask** devuelve el valor anterior de *pmode*. No se devuelve ningún error.

## <a name="remarks"></a>Comentarios

El **_umask** función establece la máscara de permisos de archivo del proceso actual en el modo especificado por *pmode*. La máscara de permisos de archivo modifica la configuración del permiso de nuevos archivos creados por **_creat**, **_open**, o **_sopen**. Si un bit de la máscara es 1, el bit correspondiente del valor de permiso solicitado del archivo se establece en 0 (no permitido). Si un bit de la máscara es 0, el bit correspondiente se deja sin modificar. La configuración de permisos de un nuevo archivo no se establece hasta que se cierra el archivo por primera vez.

La expresión de entero *pmode* contiene una o ambas de las siguientes constantes de manifiesto, definidas en SYS\STAT. H:

|*pmode*||
|-|-|
**_S_IWRITE**|Escritura permitida.
**_S_IREAD**|Lectura permitida.
**_S_IREAD** \| **_S_IWRITE**|Lectura y escritura permitidas.

Cuando ambas constantes se proporcionan, se combinan con el operador OR bit a bit ( **|** ). Si el *pmode* argumento es **_S_IREAD**, no se permite la lectura (el archivo es de solo escritura). Si el *pmode* argumento es **_S_IWRITE**, no se permite la escritura (el archivo es de solo lectura). Por ejemplo, si el bit de escritura está establecido en la máscara, los nuevos archivos serán de solo lectura. Tenga en cuenta que en los sistemas operativos MS-DOS y Windows, todos los archivos se pueden leer; no se puede conceder permiso de solo escritura. Por consiguiente, establecer la lectura de tipo bit **_umask** no tiene ningún efecto sobre los modos del archivo.

Si *pmode* no es una combinación de una de las constantes de manifiesto o incorpora un conjunto alternativo de constantes, la función simplemente omitirá los.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_umask**|\<io.h>, \<sys/stat.h>, \<sys/types.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
