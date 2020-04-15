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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 5c05d7a2743cd0c1e843d6895e8f5574031ab098
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344832"
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

*Corriente*<br/>
Flujo de entrada.

## <a name="return-value"></a>Valor devuelto

Devuelve el carácter leído. Para indicar un error de lectura o una condición de fin de archivo, **getc** devuelve **EOF**y **getwc** devuelve **WEOF**. Para **getc**, utilice **ferror** o **feof** para comprobar si hay un error o si hay fin del archivo. Si *stream* es **NULL**, **getc** y **getwc** invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EOF** (o **WEOF** para **getwc**) y **establecen errno en** **EINVAL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Observaciones

Cada rutina lee un solo carácter de un archivo en la posición actual y aumenta el puntero de archivo asociado (si se ha definido) para que apunte al carácter siguiente. El archivo está asociado con *stream*.

Estas funciones bloquean el subproceso de llamada y son, por consiguiente, seguras para subprocesos. Para obtener una versión que no sea de bloqueo, consulte [_getc_nolock, _getwc_nolock](getc-nolock-getwc-nolock.md).

Comentarios específicos de la rutina.

|Rutina|Observaciones|
|-------------|-------------|
|**getc**|Igual que **fgetc**, pero implementado como una función y como macro.|
|**getwc**|Versión de caracteres anchos de **getc**. Lee un carácter multibyte o un carácter ancho según si *la secuencia* se abre en modo de texto o en modo binario.|

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

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

### <a name="output"></a>Output

```Output
Input was: Line one.
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[_getch, _getwch](getch-getwch.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
[ungetc, ungetwc](ungetc-ungetwc.md)<br/>
