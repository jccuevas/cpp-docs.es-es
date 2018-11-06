---
title: _getw
ms.date: 11/04/2016
apiname:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: 615d3ac9bdc73ad200368eaeabf7c84951bc91ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487612"
---
# <a name="getw"></a>_getw

Obtiene un entero de una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**_getw** devuelve el valor entero leído. Un valor devuelto de **EOF** indica un error o el final del archivo. Sin embargo, dado que el **EOF** valor también es un valor entero legítimo, use **feof** o **ferror** para comprobar una condición de final de archivo o error. Si *secuencia* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **EOF**.

## <a name="remarks"></a>Comentarios

El **_getw** función lee el siguiente valor binario de tipo **int** desde el archivo asociado *secuencia* y aumenta el puntero de archivo asociado (si hay alguno) para señalar en el siguiente carácter no leído. **_getw** no supone ninguna alineación especial de los elementos de la secuencia. Pueden producirse problemas de portabilidad con **_getw** porque el tamaño de la **int** tipo y el orden de bytes en el **int** tipo difieren entre sistemas.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_getw**|\<stdio.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_getw.c
// This program uses _getw to read a word
// from a stream, then performs an error check.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   int i;

   if( fopen_s( &stream, "crt_getw.txt", "rb" ) )
      printf( "Couldn't open file\n" );
   else
   {
      // Read a word from the stream:
      i = _getw( stream );

      // If there is an error...
      if( ferror( stream ) )
      {
         printf( "_getw failed\n" );
         clearerr_s( stream );
      }
      else
         printf( "First data word in file: 0x%.4x\n", i );
      fclose( stream );
   }
}
```

### <a name="input-crtgetwtxt"></a>Entrada: crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
