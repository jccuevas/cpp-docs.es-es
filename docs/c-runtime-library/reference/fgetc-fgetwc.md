---
title: fgetc, fgetwc
ms.date: 11/04/2016
apiname:
- fgetwc
- fgetc
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
- _fgettc
- fgetwc
- fgetc
helpviewer_keywords:
- fgettc function
- characters, reading
- _fgettc function
- fgetc function
- streams, reading characters from
- reading characters from streams
- fgetwc function
ms.assetid: 13348b7b-dc86-421c-9d6c-611ca79c8338
ms.openlocfilehash: a853a46fc43106c9ea57be84b37fb46a18041ba8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62334013"
---
# <a name="fgetc-fgetwc"></a>fgetc, fgetwc

Lea un carácter de una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int fgetc(
   FILE *stream
);
wint_t fgetwc(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

**fgetc** devuelve el carácter leído como un **int** o devuelve **EOF** para indicar un error o el final del archivo. **fgetwc** devuelve, como un [wint_t](../../c-runtime-library/standard-types.md), el carácter ancho correspondiente al carácter leído, o bien devuelve **WEOF** para indicar un error o el final del archivo. Para ambas funciones, use **feof** o **ferror** para distinguir entre un error y una condición de final de archivo. Si se produce un error de lectura, se establece el indicador de error para la secuencia. Si *secuencia* es **NULL**, **fgetc** y **fgetwc** invocan el controlador de parámetros no válidos, tal y como se describe en [parámetro Validación](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **EOF**.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones lee un carácter único de la posición actual del archivo asociado con *secuencia*. A continuación, la función aumenta el puntero de archivo asociado (si está definido) para señalar al carácter siguiente. Si el flujo está al final del archivo, se establece la marca de fin de archivo para el flujo.

**fgetc** es equivalente a **getc**, pero se implementa solo como una función, en lugar de una función y una macro.

**fgetwc** es la versión de caracteres anchos de **fgetc**; lee **c** como un carácter multibyte o carácter ancho en función de si *flujo* se abre en modo de texto o modo binario.

Las versiones que tienen el sufijo **_nolock** son idénticas, salvo que no están protegidas contra las interferencias de otros subprocesos.

Para obtener más información sobre el procesamiento de caracteres anchos y caracteres multibyte en los modos binarios y de texto, consulte [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgettc**|**fgetc**|**fgetc**|**fgetwc**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fgetc**|\<stdio.h>|
|**fgetwc**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fgetc.c
// This program uses getc to read the first
// 80 input characters (or until the end of input)
// and place them into a string named buffer.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   FILE *stream;
   char buffer[81];
   int  i, ch;

   // Open file to read line from:
   fopen_s( &stream, "crt_fgetc.txt", "r" );
   if( stream == NULL )
      exit( 0 );

   // Read in first 80 characters and place them in "buffer":
   ch = fgetc( stream );
   for( i=0; (i < 80 ) && ( feof( stream ) == 0 ); i++ )
   {
      buffer[i] = (char)ch;
      ch = fgetc( stream );
   }

   // Add null to end string
   buffer[i] = '\0';
   printf( "%s\n", buffer );
   fclose( stream );
}
```

## <a name="input-crtfgetctxt"></a>Entrada: crt_fgetc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Line one.
Line two.
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputc, fputwc](fputc-fputwc.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
