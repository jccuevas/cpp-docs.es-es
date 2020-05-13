---
title: getc, getwc
ms.date: 4/2/2020
api_name:
- getwc
- getc
- _o_getc
- _o_getwc
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
- _gettc
- getwc
- _gettchar
- getc
helpviewer_keywords:
- characters, reading
- _gettc function
- getwchar function
- streams, reading characters from
- reading characters from streams
- getc function
- getwc function
- gettc function
ms.assetid: 354ef514-d0c7-404b-92f5-995f6a834bb3
ms.openlocfilehash: 6248dd2287b2f11db72f64df1241affe8deec22d
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919661"
---
# <a name="getc-getwc"></a>getc, getwc

Lea un carácter de una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int getc(
   FILE *stream
);
wint_t getwc(
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*misiones*<br/>
Flujo de entrada.

## <a name="return-value"></a>Valor devuelto

Devuelve el carácter leído. Para indicar un error de lectura o una condición de final de archivo, **GETC** devuelve **EOF**y **getwc** devuelve **WEOF**. En el caso de **GETC**, use **ferror** o **feof** para comprobar si hay un error o para el final del archivo. Si *Stream* es **null**, **GETC** y **getwc** invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EOF** (o **WEOF** para **getwc**) y establecen **errno** en **EINVAL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Observaciones

Cada rutina lee un solo carácter de un archivo en la posición actual y aumenta el puntero de archivo asociado (si se ha definido) para que apunte al carácter siguiente. El archivo está asociado a la *secuencia*.

Estas funciones bloquean el subproceso de llamada y son, por consiguiente, seguras para subprocesos. Para obtener una versión que no sea de bloqueo, consulte [_getc_nolock, _getwc_nolock](getc-nolock-getwc-nolock.md).

Comentarios específicos de la rutina.

|Rutina|Observaciones|
|-------------|-------------|
|**getc**|Igual que **fgetc**, pero se implementa como una función y como una macro.|
|**getwc**|Versión de caracteres anchos de **GETC**. Lee un carácter multibyte o un carácter ancho en función de si la *secuencia* se abre en modo de texto o en modo binario.|

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_gettc**|**getc**|**getc**|**getwc**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**getc**|\<stdio.h>|
|**getwc**|\<stdio.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_getc.c
// Use getc to read a line from a file.

#include <stdio.h>

int main()
{
    char buffer[81];
    int i, ch;
    FILE* fp;

    // Read a single line from the file "crt_getc.txt".

    fopen_s(&fp, "crt_getc.txt", "r");
    if (!fp)
    {
       printf("Failed to open file crt_getc.txt.\n");
       exit(1);
    }

    for (i = 0; (i < 80) && ((ch = getc(fp)) != EOF)
                         && (ch != '\n'); i++)
    {
        buffer[i] = (char) ch;
    }

    // Terminate string with a null character
    buffer[i] = '\0';
    printf( "Input was: %s\n", buffer);

    fclose(fp);
}
```

### <a name="input-crt_getctxt"></a>Entrada: crt_getc.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Salida

```Output
Input was: Line one.
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
