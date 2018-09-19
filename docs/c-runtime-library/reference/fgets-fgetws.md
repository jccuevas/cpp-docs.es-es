---
title: fgets, fgetws | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
dev_langs:
- C++
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab57eecfec91e277f3409ba7b9b33d99a4b52e4b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067570"
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

*secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve *str*. **NULL** se devuelve para indicar un error o una condición de final de archivo. Use **feof** o **ferror** para determinar si se produjo un error. Si *str* o *secuencia* es un puntero nulo, o *numChars* es menor o igual a cero, esta función invoca al controlador de parámetros no válidos, como se describe en [ Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **NULL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

El **fgets** función lee una cadena de la entrada *secuencia* argumento y lo almacena en *str*. **fgets** lee los caracteres de la posición actual del flujo a e incluyendo el primer carácter de nueva línea, al final de la secuencia, o hasta que el número de caracteres leídos es igual a *numChars* - 1, lo que ocurra primero. El resultado se almacena en *str* se anexa con un carácter nulo. El carácter de nueva línea, cuando se lee, se incluye en la cadena.

**fgetws** es una versión con caracteres anchos de **fgets**.

**fgetws** lee el argumento de caracteres anchos *str* como una cadena de caracteres multibyte o una cadena de caracteres anchos según si *flujo* se abre en modo de texto o binario, respectivamente. Para obtener más información sobre el uso de los modos de texto y binario en E/S de secuencias Unicode y multibyte, consulte [E/S de archivo en modo texto y en modo binario](../../c-runtime-library/text-and-binary-mode-file-i-o.md) y [E/S de secuencias Unicode en los modos binario y de texto](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).

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

### <a name="input-crtfgetstxt"></a>Entrada: crt_fgets.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Line one.
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fputs, fputws](fputs-fputws.md)<br/>
[gets, _getws](../../c-runtime-library/gets-getws.md)<br/>
[puts, _putws](puts-putws.md)<br/>
