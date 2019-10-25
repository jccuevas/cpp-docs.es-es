---
title: _setmode
ms.date: 11/04/2016
api_name:
- _setmode
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
- _setmode
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
ms.openlocfilehash: 7f14cc9451b93a9077916b8c650645990ba654a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948588"
---
# <a name="_setmode"></a>_setmode

Establece el modo de traducción del archivo.

## <a name="syntax"></a>Sintaxis

```C
int _setmode (
   int fd,
   int mode
);
```

### <a name="parameters"></a>Parámetros

*fd*<br/>
Descriptor del archivo.

*mode*<br/>
Nuevo modo de traducción.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el modo de traducción anterior.

Si se pasan parámetros no válidos a esta función, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve-1 y establece **errno** en **EBADF**, que indica un descriptor de archivo no válido, o **EINVAL**, que indica un argumento de *modo* no válido.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

La función **_setmode** *establece en el modo de* traducción del archivo proporcionado por *FD*. Al pasar **_O_TEXT** como *modo* , se establece el modo de texto (es decir, traducido). Las combinaciones de retorno de carro y avance de línea (CR-LF) se traducen en un carácter de salto de línea único en la entrada. Los caracteres de salto de línea se traducen a combinaciones CR-LF en la salida. El paso de **_O_BINARY** establece el modo binario (sin traducir), en el que se suprimen estas traducciones.

También puede pasar **_O_U16TEXT**, **_O_U8TEXT**o **_O_WTEXT** para habilitar el modo Unicode, tal como se muestra en el segundo ejemplo más adelante en este documento.

> [!CAUTION]
> El modo Unicode es para las funciones de impresión anchas `wprintf`(por ejemplo,) y no se admite para las funciones de impresión estrechas. El uso de una función de impresión estrecha en una secuencia en modo Unicode desencadena una aserción.

**_setmode** se usa normalmente para modificar el modo de traducción predeterminado de **stdin** y **stdout**, pero se puede usar en cualquier archivo. Si aplica **_setmode** al descriptor de archivo de un flujo, llame a **_setmode** antes de realizar cualquier operación de entrada o salida en la secuencia.

> [!CAUTION]
> Si escribe datos en una secuencia de archivos, vacíe explícitamente el código mediante [fflush](fflush.md) antes de usar **_setmode** para cambiar el modo. Si no vuelca el código, podría producirse un comportamiento inesperado. Si no ha escrito datos en el flujo, no será necesario volcarlo.

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
