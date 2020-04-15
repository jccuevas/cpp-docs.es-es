---
title: fgetpos
ms.date: 4/2/2020
api_name:
- fgetpos
- _o_fgetpos
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
- fgetpos
helpviewer_keywords:
- fgetpos function
- streams, file position indicator
ms.assetid: bfa05c38-1135-418c-bda1-d41be51acb62
ms.openlocfilehash: 0c16150a6240068e1453ec90b396c87ab9ece5a4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346921"
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

*Corriente*<br/>
Secuencia de destino.

*Pos*<br/>
Almacenamiento del indicador de posición.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **fgetpos** devuelve 0. En caso de error, devuelve un valor distinto de cero y establece **errno** en una de las siguientes constantes de manifiesto (definidas en STDIO. H): **EBADF**, lo que significa que la secuencia especificada no es un puntero de archivo válido o no es accesible, o **EINVAL**, lo que significa que el valor de *la secuencia* o el valor de *pos* no es válido, como si cualquiera de ellos es un puntero nulo. Si *stream* o *pos* es un puntero **NULL,** la función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Observaciones

La función **fgetpos** obtiene el valor actual del indicador de posición de archivo del argumento *stream* y lo almacena en el objeto al que apunta *pos*. La función **fsetpos** puede utilizar más adelante la información almacenada en *pos* para restablecer el puntero del argumento de *secuencia* a su posición en el momento en que se llamó a **fgetpos.** El valor *pos* se almacena en un formato interno y está pensado para su uso únicamente por **fgetpos** y **fsetpos**.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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

## <a name="input-crt_fgetpostxt"></a>Entrada: crt_fgetpos.txt

```Input
fgetpos gets a stream's file-position indicator.
```

### <a name="output-crt_fgetpostxt"></a>Salida: crt_fgetpos.txt

```Output
after fgetpos: gets a stream
after fsetpos: gets a stream
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
