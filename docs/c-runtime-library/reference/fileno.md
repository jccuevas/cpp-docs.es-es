---
title: _fileno
ms.date: 11/04/2016
api_name:
- _fileno
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fileno
helpviewer_keywords:
- file handles [C++], getting from streams
- fileno function
- _fileno function
- streams, getting file handles
ms.assetid: 86474174-2f17-4100-bcc4-352dd976c7b5
ms.openlocfilehash: 586e390e100f5dc46a49b99c007016cf23ac68f0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957202"
---
# <a name="_fileno"></a>_fileno

Obtener el descriptor de archivo asociado a un flujo

## <a name="syntax"></a>Sintaxis

```C
int _fileno(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**_fileno** devuelve el descriptor de archivo. No se devuelve ningún error. El resultado es undefined si *Stream* no especifica un archivo abierto. Si Stream es **null**, **_fileno** invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** en **EINVAL**.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

> [!NOTE]
> Si **stdout** o **stderr** no están asociados a un flujo de salida (por ejemplo, en una aplicación de Windows sin una ventana de consola), el descriptor de archivo devuelto es-2. En versiones anteriores, el descriptor de archivo devuelto era -1. Este cambio permite que las aplicaciones distingan esta condición de un error.

## <a name="remarks"></a>Comentarios

La rutina **_fileno** devuelve el descriptor de archivo asociado actualmente a la *secuencia*. Esta rutina se implementa como función y como macro. Para obtener información sobre cómo elegir una implementación, consulte [Elegir entre funciones y macros](../../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fileno**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fileno.c
// This program uses _fileno to obtain
// the file descriptor for some standard C streams.
//

#include <stdio.h>

int main( void )
{
   printf( "The file descriptor for stdin is %d\n", _fileno( stdin ) );
   printf( "The file descriptor for stdout is %d\n", _fileno( stdout ) );
   printf( "The file descriptor for stderr is %d\n", _fileno( stderr ) );
}
```

```Output
The file descriptor for stdin is 0
The file descriptor for stdout is 1
The file descriptor for stderr is 2
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_fdopen, _wfdopen](fdopen-wfdopen.md)<br/>
[_filelength, _filelengthi64](filelength-filelengthi64.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[freopen, _wfreopen](freopen-wfreopen.md)<br/>
