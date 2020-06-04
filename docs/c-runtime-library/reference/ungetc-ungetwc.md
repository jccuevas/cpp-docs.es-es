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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 406ce7d8befd1d9e9e6a065f2549bacf46d2fd6e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915980"
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

*unidad*<br/>
Carácter que se va a devolver.

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Si es correcto, cada una de estas funciones devuelve el argumento de carácter *c*. Si *c* no se puede volver a insertar o si no se ha leído ningún carácter, el flujo de entrada no cambia y **ungetc** devuelve **EOF**; **ungetwc** devuelve **WEOF**. Si *Stream* es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, se devuelve **EOF** o **WEOF** y **errno** se establece en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

La función **ungetc** vuelve a colocar el carácter *c* en la *secuencia* y borra el indicador de fin de archivo. El flujo debe estar abierto para lectura. Una operación de lectura subsiguiente en el *flujo* comienza con *c*. Se omite un intento de presionar **EOF** en la secuencia mediante **ungetc** .

Los caracteres colocados en la secuencia por **ungetc** se pueden borrar si se llama a **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**o [rebobinar](rewind.md) antes de que se lea el carácter de la secuencia. El indicador de posición de archivo tendrá el valor que tenía antes de que se volvieran a insertar los caracteres. El almacenamiento externo correspondiente al flujo no cambia. En una llamada a **ungetc** correcta en una secuencia de texto, el indicador de posición de archivo no se especifica hasta que se leen o se descartan todos los caracteres que se han vuelto a insertar. En cada llamada a **ungetc** correcta en una secuencia binaria, se reduce el indicador de posición de archivo. Si su valor era 0 antes de una llamada, el valor queda sin definir después de la llamada.

Los resultados son imprevisibles si se llama a **ungetc** dos veces sin una operación de lectura o de posicionamiento de archivo entre las dos llamadas. Después de una llamada a **fscanf**, se puede producir un error en una llamada a **ungetc** a menos que se haya realizado otra operación de lectura (por ejemplo, **GETC**). Esto se debe a que **fscanf** en sí llama a **ungetc**.

**ungetwc** es una versión con caracteres anchos de **ungetc**. Sin embargo, en cada llamada a **ungetwc** correcta en un flujo de texto o binario, el valor del indicador de posición de archivo no se especifica hasta que se leen o se descartan todos los caracteres que se han vuelto a insertar.

Estas funciones son seguras para subprocesos y bloquean los datos confidenciales durante la ejecución. Para obtener una versión que no es de bloqueo, vea [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de Plataforma universal de Windows (UWP). Los identificadores de flujo estándar que están asociados a la consola, **stdin**, **stdout**y **stderr**deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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
