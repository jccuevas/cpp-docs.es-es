---
title: _write
ms.date: 4/2/2020
api_name:
- _write
- _o__write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: a616df570d266c335337d897da59a2a0ec69b40e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367389"
---
# <a name="_write"></a>_write

Escribe datos en un archivo.

## <a name="syntax"></a>Sintaxis

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parámetros

*Fd*<br/>
Descriptor de archivo del archivo en el que se van a escribir datos.

*Búfer*<br/>
Datos que se van a escribir.

*count*<br/>
Número de bytes.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_write** devuelve el número de bytes escritos. Si el espacio real restante en el disco es menor que el tamaño del búfer que la función está intentando escribir en el disco, **_write** produce un error y no vacía el contenido del búfer en el disco. Un valor devuelto de -1 indica un error. Si se pasan parámetros no válidos, esta función invoca al controlador de parámetros no válidos, como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y **errno** se establece en uno de los tres valores: **EBADF**, lo que significa que el descriptor de archivo no es válido o el archivo no se abre para escribir; **ENOSPC**, lo que significa que no queda suficiente espacio en el dispositivo para la operación; o **EINVAL**, lo que significa que *el búfer* era un puntero nulo o que se pasó un *recuento* impar de bytes para escribirse en un archivo en modo Unicode.

Para más información sobre estos y otros códigos devueltos, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Si el archivo se abre en modo de texto, cada carácter de avance de línea se sustituye por un par de avance de línea de retorno de carro en la salida. El reemplazo no afecta al valor devuelto.

Cuando el archivo se abre en modo de traducción Unicode, por ejemplo, Si *fd* se abre mediante **_open** o **_sopen** y un parámetro de modo que incluye **_O_WTEXT**, **_O_U16TEXT**o **_O_U8TEXT**, o si se abre mediante **fopen** y un parámetro de modo que incluye **ccs-UNICODE**, **ccs-UTF-16LE**, o **ccs-UTF-8**, o si el modo se cambia a un modo de traducción mediante **_setmode**de búfer —*buffer* se interpreta como un puntero a una matriz de **wchar_t** que contiene datos **UTF-16.** Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.

## <a name="remarks"></a>Observaciones

La función **_write** escribe bytes de *recuento* desde *el búfer* en el archivo asociado a *fd*. La operación de escritura se inicia en la posición actual del puntero de archivo (si existe) asociado al archivo en cuestión. Si el archivo se abre para anexarlo, la operación comenzará en el final actual del archivo. Después de la operación de escritura, el puntero de archivo aumenta por el número de bytes escritos.

Al escribir en archivos abiertos en modo de texto, **_write** trata un carácter CTRL+Z como el extremo lógico del archivo. Al escribir en un dispositivo, **_write** trata un carácter CTRL+Z en el búfer como un terminador de salida.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_write**|\<io.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occurred
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>Consulte también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
