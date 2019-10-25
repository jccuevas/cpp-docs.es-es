---
title: _getw
ms.date: 11/04/2016
api_name:
- _getw
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
- _getw
helpviewer_keywords:
- _getw function
- integers, getting from streams
- getw function
ms.assetid: ef75facc-b84e-470f-9f5f-8746c90822a0
ms.openlocfilehash: ad03c92ce90542ecae13609ee228ad094f64fc07
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954874"
---
# <a name="_getw"></a>_getw

Obtiene un entero de una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int _getw(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**_getw** devuelve el valor entero leído. Un valor devuelto de **EOF** indica un error o el final del archivo. Sin embargo, dado que el valor **EOF** también es un valor entero legítimo, use **feof** o **ferror** para comprobar una condición de error o de final de archivo. Si *Stream* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **EOF**.

## <a name="remarks"></a>Comentarios

La función **_getw** lee el siguiente valor binario de tipo **int** del archivo asociado a *Stream* e incrementa el puntero de archivo asociado (si hay alguno) para que apunte al siguiente carácter no leído. **_getw** no supone ninguna alineación especial de los elementos de la secuencia. Los problemas de portabilidad pueden producirse con **_getw** porque el tamaño del tipo **int** y el orden de los bytes dentro del tipo **int** difieren entre los sistemas.

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

### <a name="input-crt_getwtxt"></a>Entrada: crt_getw.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Resultados

```Output
First data word in file: 0x656e694c
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_putw](putw.md)<br/>
