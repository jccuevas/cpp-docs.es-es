---
title: fgets, fgetws
ms.date: 4/2/2020
api_name:
- fgets
- fgetws
- _o_fgets
- _o_fgetws
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
ms.openlocfilehash: a1120529157801aac5cf1c4fd61f844fde443bed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346866"
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

*Str*<br/>
Ubicación de almacenamiento de los datos.

*numChars*<br/>
Número máximo de caracteres que se van a leer.

*Corriente*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve *str*. **NULL** se devuelve para indicar un error o una condición de fin de archivo. Utilice **feof** o **ferror** para determinar si se ha producido un error. Si *str* o *stream* es un puntero nulo, o *numChars* es menor o igual que cero, esta función invoca el controlador de parámetros no válidos, como se describe en [validación](../../c-runtime-library/parameter-validation.md)de parámetros . Si la ejecución puede continuar, **errno** se establece **en EINVAL** y la función devuelve **NULL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Observaciones

La función **fgets** lee una cadena del argumento de *secuencia* de entrada y la almacena en *str*. **fgets** lee caracteres de la posición actual de la secuencia a e incluyendo el primer carácter de nueva línea, hasta el final de la secuencia, o hasta que el número de caracteres leídos es igual a *numChars* - 1, lo que ocurra primero. El resultado almacenado en *str* se anexa con un carácter nulo. El carácter de nueva línea, cuando se lee, se incluye en la cadena.

**fgetws** es una versión de **caracteres anchos de fgets.**

**fgetws** lee el argumento de caracteres anchos *str* como una cadena de caracteres múltiples o una cadena de caracteres anchos según si *la secuencia* se abre en modo de texto o en modo binario, respectivamente. Para obtener más información sobre el uso de los modos de texto y binario en E/S de secuencias Unicode y multibyte, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fgetts**|**fgets**|**fgets**|**fgetws**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fgets**|\<stdio.h>|
|**fgetws**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

### <a name="output"></a>Output

```Output
Line one.
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[obtiene, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
