---
title: _tell, _telli64 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _telli64
- _tell
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tell
- telli64
- _telli64
- _tell
dev_langs:
- C++
helpviewer_keywords:
- tell function
- file pointers [C++], getting
- _tell function
- file pointers [C++]
- telli64 function
- _telli64 function
ms.assetid: 1500e8f9-8fec-4253-9eec-ec66125dfc9b
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85586a4c0c3a1a035dc4ccb1d36b2fed415220cd
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="tell-telli64"></a>_tell, _telli64

Obtiene la posición del puntero de archivo.

## <a name="syntax"></a>Sintaxis

```C
long _tell(
   int handle
);
__int64 _telli64(
   int handle
);
```

### <a name="parameters"></a>Parámetros

*Identificador*<br/>
Descriptor de archivo que hace referencia a un archivo abierto.

## <a name="return-value"></a>Valor devuelto

Posición actual del puntero de archivo. En los dispositivos incapaces de efectuar búsquedas, el valor devuelto es indefinido.

Un valor devuelto de-1 L indica un error. Si *controlar* es un descriptor de archivo no válido, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EBADF** y devuelven-1 L.

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

El **_tell** función obtiene la posición actual del puntero de archivo (si existe) asociada a la *controlar* argumento. La posición se expresa como el número de bytes desde el principio del archivo. Para el **_telli64** función, este valor se expresa como un entero de 64 bits.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_tell**, **_telli64**|\<io.h>|

Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_tell.c
// This program uses _tell to tell the
// file pointer position after a file read.
//

#include <io.h>
#include <stdio.h>
#include <fcntl.h>
#include <share.h>
#include <string.h>

int main( void )
{
   int  fh;
   char buffer[500];

   if ( _sopen_s( &fh, "crt_tell.txt", _O_RDONLY, _SH_DENYNO, 0) )
   {
      char buff[50];
      _strerror_s( buff, sizeof(buff), NULL );
      printf( buff );
      exit( -1 );
   }

   if( _read( fh, buffer, 500 ) > 0 )
      printf( "Current file position is: %d\n", _tell( fh ) );
   _close( fh );
}
```

### <a name="input-crttelltxt"></a>Entrada: crt_tell.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Current file position is: 20
```

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[ftell, _ftelli64](ftell-ftelli64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
