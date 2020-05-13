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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: b57a07dbe5c2c746e8af6b96f1864e4f4534849f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920362"
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

*misiones*<br/>
Secuencia de destino.

*abre*<br/>
Almacenamiento del indicador de posición.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, **fgetpos** devuelve 0. En caso de error, devuelve un valor distinto de cero y establece **errno** en una de las siguientes constantes de manifiesto (definidas en stdio. H): **EBADF**, que significa que la secuencia especificada no es un puntero de archivo válido o no es accesible, o **EINVAL**, lo que significa que el valor de *flujo* o el valor de *pos* no es válido, por ejemplo, si es un puntero nulo. Si *Stream* o *pos* es un puntero **nulo** , la función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

## <a name="remarks"></a>Observaciones

La función **fgetpos** obtiene el valor actual del indicador de posición de archivo del argumento de *flujo* y lo almacena en el objeto al que apunta *pos*. La función **fsetpos** puede usar posteriormente la información almacenada en el *PDV* para restablecer el puntero del argumento de *flujo* a su posición en el momento en que se llamó a **fgetpos** . El valor de *pos* se almacena en un formato interno y está pensado para su uso exclusivo de **fgetpos** y **fsetpos**.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

## <a name="see-also"></a>Consulta también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fsetpos](fsetpos.md)<br/>
