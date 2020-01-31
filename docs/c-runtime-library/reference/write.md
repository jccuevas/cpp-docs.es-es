---
title: _write
ms.date: 11/04/2016
api_name:
- _write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 5eaee64c1bf6ad4b4d59c3a7b1a1434741e74454
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821797"
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

### <a name="parameters"></a>Parameters

*fd*<br/>
Descriptor de archivo del archivo en el que se van a escribir datos.

*buffer*<br/>
Datos que se van a escribir.

*count*<br/>
Número de bytes.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **_write** devuelve el número de bytes escritos. Si el espacio real que queda en el disco es menor que el tamaño del búfer que la función está intentando escribir en el disco, **_write** produce un error y no vacía el contenido del búfer en el disco. Un valor devuelto de-1 indica un error. Si se pasan parámetros no válidos, esta función invoca al controlador de parámetros no válidos, como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve-1 y **errno** se establece en uno de estos tres valores: **EBADF**, lo que significa que el descriptor de archivo no es válido o que el archivo no está abierto para escritura. **ENOSPC**, lo que significa que no queda suficiente espacio en el dispositivo para la operación; o **EINVAL**, lo que significa que el *búfer* era un puntero nulo o que se pasó un *recuento* impar de bytes para que se escriba en un archivo en modo Unicode.

Para más información sobre estos y otros códigos devueltos, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

Si el archivo se abre en modo de texto, cada carácter de avance de línea se reemplaza por un par de retorno de carro y avance de línea en la salida. El reemplazo no afecta al valor devuelto.

Cuando el archivo se abre en el modo de conversión Unicode (por ejemplo, si se abre *FD* con **_open** o **_sopen** y un parámetro de modo que incluye **_O_WTEXT**, **_O_U16TEXT**, o **_O_U8TEXT**, o si se abre mediante **fopen** y un parámetro de modo que incluye **CCS = Unicode**, **CCS = UTF-16LE**o **CCS = UTF-8**, o si el modo se cambia a un modo de conversión Unicode mediante **_setmode**; el*búfer* se interpreta como un puntero a un matriz de **wchar_t** que contiene datos **UTF-16** . Si se intenta escribir un número impar de bytes en este modo, se producirá un error de validación de parámetros.

## <a name="remarks"></a>Notas

La función **_write** escribe bytes de *recuento* desde el *búfer* en el archivo asociado a *FD*. La operación de escritura se inicia en la posición actual del puntero de archivo (si existe) asociado al archivo en cuestión. Si el archivo se abre para anexarlo, la operación comenzará en el final actual del archivo. Después de la operación de escritura, el puntero de archivo aumenta en función del número de bytes escritos.

Cuando se escribe en archivos abiertos en modo de texto, **_write** trata un carácter Ctrl + Z como el final lógico del archivo. Al escribir en un dispositivo, **_write** trata un carácter Ctrl + Z en el búfer como un terminador de salida.

## <a name="requirements"></a>Requisitos de

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

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
