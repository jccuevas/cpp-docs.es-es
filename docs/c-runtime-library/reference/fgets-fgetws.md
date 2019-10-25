---
title: fgets, fgetws
ms.date: 07/11/2018
api_name:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
ms.openlocfilehash: 3f68bee181ebb20eb7a0a2eaca02a72c4dc03616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957401"
---
# <a name="fgets-fgetws"></a>fgets, fgetws

Obtiene una cadena de una secuencia.

## <a name="syntax"></a>Sintaxis

```C
char *fgets(
   char *str,
   int numChars,
   FILE *stream
);
wchar_t *fgetws(
   wchar_t *str,
   int numChars,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*str*<br/>
Ubicación de almacenamiento de los datos.

*numChars*<br/>
Número máximo de caracteres que se van a leer.

*stream*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve *Str*. Se devuelve **null** para indicar un error o una condición de final de archivo. Use **feof** o **ferror** para determinar si se ha producido un error. Si *Str* o *Stream* es un puntero nulo, o *numChars* es menor o igual que cero, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **null**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

La función **fgets** Lee una cadena del argumento de *flujo* de entrada y la almacena en *Str*. **fgets** Lee los caracteres de la posición actual de la secuencia hasta el primer carácter de nueva línea, hasta el final de la secuencia, o hasta que el número de caracteres leídos sea igual a *numChars* -1, lo que suceda primero. El resultado almacenado en *Str* se anexa con un carácter nulo. El carácter de nueva línea, cuando se lee, se incluye en la cadena.

**fgetws** es una versión con caracteres anchos de **fgets**.

**fgetws** lee el argumento de caracteres anchos *Str* como una cadena de caracteres multibyte o una cadena de caracteres anchos en función de si la *secuencia* se abre en modo de texto o en modo binario, respectivamente. Para obtener más información sobre el uso de los modos de texto y binario en E/S de secuencias Unicode y multibyte, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fgets.c
// This program uses fgets to display
// the first line from a file.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[100];

   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )
   {
      if( fgets( line, 100, stream ) == NULL)
         printf( "fgets error\numChars" );
      else
         printf( "%s", line);
      fclose( stream );
   }
}
```

### <a name="input-crt_fgetstxt"></a>Entrada: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Resultados

```Output
Line one.
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
