---
title: _read | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _read
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
- _read
dev_langs:
- C++
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c67ce8ac0e754bf3003b23c56cd1d3f428be903
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="read"></a>_read

Lee datos desde un archivo.

## <a name="syntax"></a>Sintaxis

```C
int _read(
   int fd,
   void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>Parámetros

*FD*<br/>
Descriptor de archivo que hace referencia al archivo abierto.

*buffer*<br/>
Ubicación de almacenamiento de los datos.

*count*<br/>
Número máximo de bytes.

## <a name="return-value"></a>Valor devuelto

**_read** devuelve el número de bytes leídos, que puede ser menor que *recuento* si hay menos de *recuento* bytes restante en el archivo o si el archivo se abre en modo de texto, en cuyo caso cada carro valor devuelto y par '\r\n' de avance de línea se sustituye por un carácter de avance de línea único '\n'. Solo se cuenta el carácter de avance de línea en el valor devuelto. El reemplazo no afecta al puntero de archivo.

Si la función intenta leer al final del archivo, devuelve 0. Si *fd* es no válida, el archivo no está abierto para lectura, o el archivo está bloqueado, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y establece **errno** a **EBADF**.

Si *buffer* es **NULL**, se invoca al controlador de parámetros no válidos. Si la ejecución puede continuar, la función devuelve -1 y **errno** está establecido en **EINVAL**.

Para obtener más información sobre este y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **_preguntas** función lee un máximo de *recuento* bytes en *búfer* desde el archivo asociado a *fd*. La operación de lectura se inicia en la posición actual del puntero de archivo asociado al archivo en cuestión. Después de la operación de lectura, el puntero de archivo señala al siguiente carácter no leído.

Si el archivo se abre en modo de texto, la operación de lectura finaliza cuando **_read** encuentra un carácter CTRL+Z, que se trata como un indicador de fin de archivo. Use [_lseek](lseek-lseeki64.md) para borrar el indicador de fin de archivo.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_read**|\<io.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh;
   unsigned int nbytes = 60000, bytesread;

   /* Open file for input: */
   if( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if( ( bytesread = _read( fh, buffer, nbytes ) ) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crtreadtxt"></a>Entrada: crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>Vea también

[E/S de bajo nivel](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
