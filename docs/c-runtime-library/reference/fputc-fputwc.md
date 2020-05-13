---
title: fputc, fputwc
ms.date: 4/2/2020
api_name:
- fputc
- fputwc
- _o_fputc
- _o_fputwc
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
- fputc
- fputwc
- _fputtc
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
ms.openlocfilehash: 90091bff6a8ee3ced050c359ed540f45afe74f6b
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910204"
---
# <a name="fputc-fputwc"></a>fputc, fputwc

Escribe un carácter en un flujo.

## <a name="syntax"></a>Sintaxis

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>Parámetros

*unidad*<br/>
Carácter que se va a escribir.

*misiones*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el carácter escrito. En el caso de **fputc**, un valor devuelto de **EOF** indica un error. En el caso de **fputwc**, un valor devuelto de **WEOF** indica un error. Si *Stream* es **null**, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelven **EOF** y establecen **errno** en **EINVAL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Observaciones

Cada una de estas funciones escribe el carácter *c* en un archivo en la posición indicada por el indicador de posición de archivo asociado (si está definido) y hace avanzar el indicador según corresponda. En el caso de **fputc** y **fputwc**, el archivo está asociado a *Stream*. Si el archivo no admite solicitudes de posición o no se abrió en modo Append, el carácter se anexa al final del flujo.

Las dos funciones se comportan igual si el flujo se abre en modo ANSI. **fputc** no admite actualmente la salida en un flujo Unicode.

Las versiones que tienen el sufijo **_nolock** son idénticas, salvo que no están protegidas contra las interferencias de otros subprocesos. Para obtener más información, consulte [_fputc_nolock, _fputwc_nolock](fputc-nolock-fputwc-nolock.md).

Comentarios específicos de la rutina.

|Rutina|Observaciones|
|-------------|-------------|
|**fputc**|Equivalente a **putc**, pero implementado solo como función, en lugar de como una función y una macro.|
|**fputwc**|Versión de caracteres anchos de **fputc**. Escribe *c* como carácter multibyte o carácter ancho en función de si la *secuencia* se abre en modo de texto o en modo binario.|

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de Plataforma universal de Windows (UWP). Se deben redirigir los identificadores de flujo estándar que están asociados a la consola (**stdin**, **stdout**y **stderr**) antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
