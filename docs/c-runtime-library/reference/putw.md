---
title: _putw
ms.date: 4/2/2020
api_name:
- _putw
- _o__putw
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
- _putw
helpviewer_keywords:
- integers, writing to streams
- putw function
- streams, writing integers to
- _putw function
ms.assetid: 83d63644-249d-4a39-87e5-3b7aa313968d
ms.openlocfilehash: c54490a5625bfa2f9ffc95d616c2d73a7acf98e5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82916083"
---
# <a name="_putw"></a>_putw

Escribe un entero en una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int _putw(
   int binint,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*binint*<br/>
Entero binario que se generará.

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Devuelve el valor escrito. Un valor devuelto de **EOF** puede indicar un error. Dado que **EOF** también es un valor entero legítimo, use **ferror** para comprobar un error. Si *Stream* es un puntero nulo, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve **EOF**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **_putw** escribe un valor binario de tipo **int** en la posición actual de la *secuencia.* **_putw** no afecta a la alineación de los elementos de la secuencia ni supone ninguna alineación especial. **_putw** es principalmente para la compatibilidad con bibliotecas anteriores. Pueden producirse problemas de portabilidad con **_putw** porque el tamaño de un **int** y el orden de los bytes dentro de un **int** difieren entre los sistemas.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_putw**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_putw.c
/* This program uses _putw to write a
* word to a stream, then performs an error check.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   unsigned u;
   if( fopen_s( &stream, "data.out", "wb" ) )
      exit( 1 );
   for( u = 0; u < 10; u++ )
   {
      _putw( u + 0x2132, stream );   /* Write word to stream. */
      if( ferror( stream ) )         /* Make error check. */
      {
         printf( "_putw failed" );
         clearerr_s( stream );
         exit( 1 );
      }
   }
   printf( "Wrote ten words\n" );
   fclose( stream );
}
```

### <a name="output"></a>Salida

```Output
Wrote ten words
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_getw](getw.md)<br/>
