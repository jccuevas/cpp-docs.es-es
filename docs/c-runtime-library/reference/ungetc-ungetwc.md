---
title: ungetc, ungetwc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- ungetwc
- ungetc
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
- _ungettc
- ungetwc
- ungetc
dev_langs:
- C++
helpviewer_keywords:
- ungetwc function
- ungettc function
- characters, pushing back onto stream
- _ungettc function
- ungetc function
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6618e3e92d605d9e706331b44b352b41d29d6a61
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32414592"
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

*c*<br/>
Carácter que se va a devolver.

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Si es correcto, cada una de estas funciones devuelve el argumento de carácter *c*. Si *c* no se puede volver a insertar o si no se ha leído ningún carácter, el flujo de entrada no cambia y **ungetc** devuelve ** EOF`; **ungetwc` devuelve **WEOF**. Si *flujo* es **NULL**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **EOF** o **WEOF** se devuelve y **errno** está establecido en **EINVAL**.

Para obtener información sobre estos y otros códigos de error, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **ungetc** función inserta el carácter *c* a *flujo* y borra el indicador de fin de archivo. El flujo debe estar abierto para lectura. Siguiente operación de lectura en *flujo* comienza con *c*. Intentos de insertar **EOF** en el flujo mediante **ungetc** se omite.

Caracteres que se colocan en el flujo **ungetc** se podrían borrar si **fflush**, [fseek](fseek-fseeki64.md), **fsetpos**, o [rebobinar](rewind.md) se llama antes de que el carácter se lee de la secuencia. El indicador de posición de archivo tendrá el valor que tenía antes de que se volvieran a insertar los caracteres. El almacenamiento externo correspondiente al flujo no cambia. En una correcta **ungetc** llamada en una secuencia de texto, el indicador de posición de archivo no está especificado hasta que todos los caracteres vuelto se leen o se descartan. En cada uno de ellos correcta **ungetc** llamada en una secuencia binaria, el indicador de posición de archivo es reducido; si el valor era 0 antes de la llamada, el valor es indefinido después de la llamada.

Los resultados son impredecibles si **ungetc** se llama dos veces sin una lectura o la operación de posicionamiento de archivo entre las dos llamadas. Después de llamar a **fscanf**, una llamada a **ungetc** puede producir un error a menos que otra operación de lectura (como **getc**) se ha realizado. Esto es porque **fscanf** por sí mismo llama **ungetc**.

**ungetwc** es una versión con caracteres anchos de **ungetc**. Sin embargo, en cada uno de ellos correcta **ungetwc** llamada en un flujo de texto o binario, el valor del indicador de posición de archivo no está especificado hasta que se leen o se descartan todos los caracteres de vuelto.

Estas funciones son seguras para subprocesos y bloquean los datos confidenciales durante la ejecución. Para obtener una versión que no es de bloqueo, vea [_ungetc_nolock, _ungetwc_nolock](ungetc-nolock-ungetwc-nolock.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ungettc**|**ungetc**|**ungetc**|**ungetwc**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**ungetc**|\<stdio.h>|
|**ungetwc**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[getc, getwc](getc-getwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
