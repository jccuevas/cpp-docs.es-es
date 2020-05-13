---
title: ftell, _ftelli64
ms.date: 4/2/2020
api_name:
- _ftelli64
- ftell
- _o__ftelli64
- _o_ftell
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _ftelli64
- ftell
helpviewer_keywords:
- ftell function
- ftelli64 function
- _ftelli64 function
- file pointers [C++], getting current position
- file pointers [C++]
ms.assetid: 40149cd8-65f2-42ff-b70c-68e3e918cdd7
ms.openlocfilehash: 273ad4990f78355029770e19e7cdcf36d7ba39bf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910078"
---
# <a name="ftell-_ftelli64"></a>ftell, _ftelli64

Obtiene la posición actual de un puntero de archivo.

## <a name="syntax"></a>Sintaxis

```C
long ftell(
   FILE *stream
);
__int64 _ftelli64(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*misiones*<br/>
Estructura del **archivo** de destino.

## <a name="return-value"></a>Valor devuelto

**ftell** y **_ftelli64** devuelven la posición del archivo actual. Es posible que el valor devuelto por **ftell** y **_ftelli64** no refleje el desplazamiento de bytes físicos de las secuencias abiertas en modo de texto, porque el modo de texto produce una conversión de retorno de carro y avance de línea. Use **ftell** con [fseek](fseek-fseeki64.md) o **_ftelli64** con [_fseeki64](fseek-fseeki64.md) para volver a las ubicaciones de archivos correctamente. En el error, **ftell** y **_ftelli64** invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven-1L y establecen **errno** en una de dos constantes, definidas en errno. C. La constante **EBADF** significa que el argumento de *secuencia* no es un valor de puntero de archivo válido o no hace referencia a un archivo abierto. **EINVAL** significa que se pasó un argumento de *secuencia* no válido a la función. En los dispositivos que no pueden realizar búsquedas (como terminales e impresoras) o cuando *Stream* no hace referencia a un archivo abierto, el valor devuelto es indefinido.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

Las funciones **ftell** y **_ftelli64** recuperan la posición actual del puntero de archivo (si existe) asociado a la *secuencia*. La posición se expresa como un desplazamiento en relación con el principio del flujo.

Tenga en cuenta que cuando un archivo se abre para anexar datos, la posición de archivo actual se determina con la última operación de E/S, no en función de dónde se produciría la siguiente escritura. Por ejemplo, si un archivo se abre para anexar y la última operación fue de lectura, la posición de archivo es el punto donde empezaría la siguiente operación de lectura, no donde empezaría la siguiente escritura. (Cuando un archivo se abre para anexar, la posición del archivo se mueve al final del archivo antes de cualquier operación de escritura). Si todavía no se ha producido ninguna operación de e/s en un archivo abierto para anexar, la posición del archivo es el principio del archivo.

En modo de texto, CTRL+Z se interpreta como un carácter de final de archivo en la entrada. En los archivos abiertos para lectura/escritura, **fopen** y todas las rutinas relacionadas comprueban si hay un Ctrl + Z al final del archivo y lo quitan si es posible. Esto se hace porque el uso de la combinación de **ftell** y [fseek](fseek-fseeki64.md) o **_ftelli64** y [_fseeki64](fseek-fseeki64.md), para moverse dentro de un archivo que finaliza con CTRL + Z puede hacer que **ftell** o **_ftelli64** se comporten de forma incorrecta cerca del final del archivo.

Esta función bloquea el subproceso de llamada durante la ejecución y por lo tanto es segura para subprocesos. Para obtener una versión que no sea de bloqueo, consulte **_ftell_nolock**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|Encabezados opcionales|
|--------------|---------------------|----------------------|
|**ftell**|\<stdio.h>|\<errno.h>|
|**_ftelli64**|\<stdio.h>|\<errno.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_ftell.c
// This program opens a file named CRT_FTELL.C
// for reading and tries to read 100 characters. It
// then uses ftell to determine the position of the
// file pointer and displays this position.

#include <stdio.h>

FILE *stream;

int main( void )
{
   long position;
   char list[100];
   if( fopen_s( &stream, "crt_ftell.c", "rb" ) == 0 )
   {
      // Move the pointer by reading data:
      fread( list, sizeof( char ), 100, stream );
      // Get position after read:
      position = ftell( stream );
      printf( "Position after trying to read 100 bytes: %ld\n",
              position );
      fclose( stream );
   }
}
```

```Output
Position after trying to read 100 bytes: 100
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[fgetpos](fgetpos.md)<br/>
[fseek, _fseeki64](fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](lseek-lseeki64.md)<br/>
