---
title: ungetc, ungetwc
ms.date: 4/2/2020
api_name:
- ungetwc
- ungetc
- _o_ungetc
- _o_ungetwc
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
- _ungettc
- ungetwc
- ungetc
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
ms.openlocfilehash: 484af7b72f860a8a9d12cf0b62444871caad4675
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361296"
---
# <a name="ungetc-ungetwc"></a>ungetc, ungetwc

Vuelve a insertar un carácter en el flujo.

## <a name="syntax"></a>Sintaxis

```C
int ungetc(
   int c,
   FILE *stream
);
wint_t ungetwc(
   wint_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Carácter que se va a devolver.

*Corriente*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, cada una de estas funciones devuelve el argumento de carácter *c*. Si *c* no se puede retroceder o si no se ha leído ningún carácter, la secuencia de entrada no cambia y **ungetc** devuelve **EOF**; **ungetwc** devuelve **WEOF**. Si *stream* es **NULL**, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, se devuelve **EOF** o **WEOF** y **errno** se establece **en EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **ungetc** inserta el carácter *c* de nuevo en la *secuencia* y borra el indicador de fin de archivo. El flujo debe estar abierto para lectura. Una operación de lectura posterior en *la secuencia* comienza con *c*. Se omite un intento de insertar **EOF** en la secuencia mediante **ungetc.**

Los caracteres colocados en la secuencia por **ungetc** se pueden borrar si se llama a **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**o [rewind](rewind.md) antes de que el carácter se lea de la secuencia. El indicador de posición de archivo tendrá el valor que tenía antes de que se volvieran a insertar los caracteres. El almacenamiento externo correspondiente al flujo no cambia. En una llamada **ungetc** correcta en una secuencia de texto, el indicador de posición de archivo no se especifica hasta que se leen o descartan todos los caracteres insertados. En cada llamada **ungetc** correcta contra una secuencia binaria, el indicador de posición de archivo se reduce; si su valor era 0 antes de una llamada, el valor es indefinido después de la llamada.

Los resultados son impredecibles si se llama a **ungetc** dos veces sin una operación de lectura o posicionamiento de archivos entre las dos llamadas. Después de una llamada a **fscanf**, una llamada a **ungetc** puede fallar a menos que se haya realizado otra operación de lectura (como **getc ).** Esto se debe a que **fscanf** llama **ungetc**.

**ungetwc** es una versión de caracteres anchos de **ungetc**. Sin embargo, en cada llamada **ungetwc** correcta contra un texto o una secuencia binaria, el valor del indicador de posición de archivo no se especifica hasta que se leen o descartan todos los caracteres de represión.

Estas funciones son seguras para subprocesos y bloquean los datos confidenciales durante la ejecución. Para obtener una versión que no es de bloqueo, vea [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la Plataforma universal de Windows (UWP). Los identificadores de secuencia estándar asociados a la consola, **stdin,** **stdout**y **stderr**, deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_ungetc.c
// This program first converts a character
// representation of an unsigned integer to an integer. If
// the program encounters a character that is not a digit,
// the program uses ungetc to replace it in the  stream.
//

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   int result = 0;

   // Read in and convert number:
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )
      result = result * 10 + ch - '0';    // Use digit.
   if( ch != EOF )
      ungetc( ch, stdin );                // Put nondigit back.
   printf( "Number = %d\nNext character in stream = '%c'",
            result, getchar() );
}
```

```Output

      521aNumber = 521
Next character in stream = 'a'
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
