---
title: fgetpos
ms.date: 11/04/2016
apiname:
- fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: e213c9830ffe6edf04b12a80828f14cc48f77524
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658424"
---
# <a name="fgetpos"></a>fgetpos

Obtiene un indicador de posición de archivo de la secuencia.

## <a name="syntax"></a>Sintaxis

```C
int fgetpos(
   FILE *stream,
   fpos_t *pos
);
```

### <a name="parameters"></a>Parámetros

*secuencia*<br/>
Secuencia de destino.

*punto de venta*<br/>
Almacenamiento del indicador de posición.

## <a name="return-value"></a>Valor devuelto

Si es correcto, **fgetpos** devuelve 0. En caso de error, devuelve un valor distinto de cero y establece **errno** a uno de los siguientes (definidas en STDIO de constantes del manifiesto. (H): **EBADF**, lo que significa que la secuencia especificada no es un puntero de archivo válido o no está accesible, o **EINVAL**, lo que significa que el *secuencia* valor o el valor de *pos* es válido, por ejemplo, si bien es un puntero nulo. Si *secuencia* o *pos* es un **NULL** puntero, la función invoca al controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Comentarios

El **fgetpos** función obtiene el valor actual de la *secuencia* indicador de posición de archivo y la almacena en el objeto que apunta del argumento *pos*. El **fsetpos** función puede usar más adelante información almacenada en *pos* para restablecer la *secuencia* puntero del argumento en su posición en el momento **fgetpos** llamó. El *pos* valor se almacena en un formato interno y está pensado para usarse únicamente por **fgetpos** y **fsetpos**.

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fgetpos**|\<stdio.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fgetpos.c
// This program uses fgetpos and fsetpos to
// return to a location in a file.

#include <stdio.h>

int main( void )
{
   FILE   *stream;
   fpos_t pos;
   char   buffer[20];

   if( fopen_s( &stream, "crt_fgetpos.txt", "rb" ) ) {
      perror( "Trouble opening file" );
      return -1;
   }

   // Read some data and then save the position.
   fread( buffer, sizeof( char ), 8, stream );
   if( fgetpos( stream, &pos ) != 0 ) {
      perror( "fgetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fgetpos: %.13s\n", buffer );

   // Restore to old position and read data
   if( fsetpos( stream, &pos ) != 0 ) {
      perror( "fsetpos error" );
      return -1;
   }

   fread( buffer, sizeof( char ), 13, stream );
   printf( "after fsetpos: %.13s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetpostxt"></a>Entrada: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crtfgetpostxt"></a>Salida: crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
