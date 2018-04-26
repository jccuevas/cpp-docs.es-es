---
title: _setmode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _setmode
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
- _setmode
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44b17b7b6fe579d9266c98aeb410b30b94f9b136
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="setmode"></a>_setmode

Establece el modo de traducción del archivo.

## <a name="syntax"></a>Sintaxis

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parámetros

*FD*<br/>
Descriptor del archivo.

*mode*<br/>
Nuevo modo de traducción.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el modo de traducción anterior.

Si se pasan parámetros no válidos a esta función, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** como **EBADF**, lo que indica un descriptor de archivo no válido o **EINVAL**, que indica un válido *modo* argumento.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_setmode** función establece en *modo* el modo de traducción de archivo indicado por *fd*. Pasar **_O_TEXT** como *modo* establece texto (Esto es, traducido) modo. Carro retorno-combinaciones de línea (CR-LF) se convierten en una sola línea carácter de salto en la entrada. Los caracteres de salto de línea se traducen a combinaciones CR-LF en la salida. Pasar **_O_BINARY** establece binario (sin traducir) el modo, en el que se eliminan las traducciones.

También puede pasar **_O_U16TEXT**, **_O_U8TEXT**, o **_O_WTEXT** para habilitar el modo Unicode, como se muestra en el segundo ejemplo más adelante en este documento. **_setmode** se utiliza normalmente para modificar el modo de traducción predeterminado de **stdin** y **stdout**, pero se puede usar en cualquier archivo. Si aplica **_setmode** al descriptor de archivo de un flujo, llame a **_setmode** antes de realizar cualquier operación de entrada o salida en la secuencia.

> [!CAUTION]
> Si escribe datos en una secuencia de archivo, vaciar explícitamente el código mediante el uso de [fflush](fflush.md) antes de usar **_setmode** para cambiar el modo. Si no vuelca el código, podría producirse un comportamiento inesperado. Si no ha escrito datos en el flujo, no será necesario volcarlo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_setmode.c
// This program uses _setmode to change
// stdin from text mode to binary mode.

#include <stdio.h>
#include <fcntl.h>
#include <io.h>

int main( void )
{
   int result;

   // Set "stdin" to have binary mode:
   result = _setmode( _fileno( stdin ), _O_BINARY );
   if( result == -1 )
      perror( "Cannot set mode" );
   else
      printf( "'stdin' successfully changed to binary mode\n" );
}
```

```Output
'stdin' successfully changed to binary mode
```

## <a name="example"></a>Ejemplo

```C
// crt_setmodeunicode.c
// This program uses _setmode to change
// stdout to Unicode. Cyrillic and Ideographic
// characters will appear on the console (if
// your console font supports those character sets).

#include <fcntl.h>
#include <io.h>
#include <stdio.h>

int main(void) {
    _setmode(_fileno(stdout), _O_U16TEXT);
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");
    return 0;
}
```

## <a name="see-also"></a>Vea también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
