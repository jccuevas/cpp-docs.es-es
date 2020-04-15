---
title: _setmode
ms.date: 4/2/2020
api_name:
- _setmode
- _o__setmode
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 36d2130d4039f1f87f7f54fc26ad02cb8d519b4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353835"
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

*Fd*<br/>
Descriptor del archivo.

*Modo*<br/>
Nuevo modo de traducción.

## <a name="return-value"></a>Valor devuelto

Si es correcto, devuelve el modo de traducción anterior.

Si se pasan parámetros no válidos a esta función, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función devuelve -1 y establece **errno** en **EBADF**, que indica un descriptor de archivo no válido, o **EINVAL**, que indica un argumento de *modo* no válido.

Para obtener más información sobre estos y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_setmode** establece en *el modo* el modo de traducción del archivo dado por *fd*. Pasar **_O_TEXT** como *modo* establece el modo de texto (es decir, traducido). Las combinaciones de avance de línea de retorno de carro (CR-LF) se traducen en un carácter de avance de línea único en la entrada. Los caracteres de salto de línea se traducen a combinaciones CR-LF en la salida. Al pasar **_O_BINARY** establece el modo binario (sin traducir), en el que se suprimen estas traducciones.

También puede pasar **_O_U16TEXT**, **_O_U8TEXT**o **_O_WTEXT** para habilitar el modo Unicode, como se muestra en el segundo ejemplo más adelante en este documento.

> [!CAUTION]
> El modo Unicode es para funciones de impresión amplias (por ejemplo, `wprintf`) y no es compatible con funciones de impresión estrechas. El uso de una función de impresión estrecha en una secuencia de modo Unicode desencadena una aserción.

**_setmode** se utiliza normalmente para modificar el modo de traducción predeterminado de **stdin** y **stdout**, pero se puede utilizar en cualquier archivo. Si aplica **_setmode** al descriptor de archivo de una secuencia, llame a **_setmode** antes de realizar cualquier operación de entrada o salida en la secuencia.

> [!CAUTION]
> Si escribe datos en una secuencia de archivos, vacíe explícitamente el código mediante [fflush](fflush.md) antes de usar **_setmode** para cambiar el modo. Si no vuelca el código, podría producirse un comportamiento inesperado. Si no ha escrito datos en el flujo, no será necesario volcarlo.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezados opcionales|
|-------------|---------------------|----------------------|
|**_setmode**|\<io.h>|\<fcntl.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Consulte también

[Control de archivos](../../c-runtime-library/file-handling.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_set_fmode](set-fmode.md)<br/>
