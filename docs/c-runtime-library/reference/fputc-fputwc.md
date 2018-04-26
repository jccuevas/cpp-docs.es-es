---
title: fputc, fputwc | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fputc
- fputwc
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
- fputc
- fputwc
- _fputtc
dev_langs:
- C++
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 707c6d7fa2e45a4fb0c841015f59ef786e539168
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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

*c*<br/>
Carácter que se va a escribir.

*Secuencia*<br/>
Puntero a la estructura **FILE**.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el carácter escrito. Para **fputc**, un valor devuelto de **EOF** indica un error. Para **fputwc**, un valor devuelto de **WEOF** indica un error. Si *flujo* es **NULL**, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelven **EOF** y establecer **errno** a **EINVAL**.

Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

## <a name="remarks"></a>Comentarios

Cada una de estas funciones escribe el carácter único *c* a un archivo en la posición indicada por el indicador de posición de archivo asociado (si se ha definido) y hace avanzar el indicador según corresponda. En el caso de **fputc** y **fputwc**, está asociado el archivo *flujo*. Si el archivo no admite solicitudes de posición o no se abrió en modo Append, el carácter se anexa al final del flujo.

Las dos funciones se comportan igual si el flujo se abre en modo ANSI. **fputc** no admite actualmente la salida en un flujo UNICODE.

Las versiones que tienen el sufijo **_nolock** son idénticas, salvo que no están protegidas contra las interferencias de otros subprocesos. Para obtener más información, consulte [_fputc_nolock, _fputwc_nolock](fputc-nolock-fputwc-nolock.md).

Comentarios específicos de la rutina.

|Rutina|Comentarios|
|-------------|-------------|
|**fputc**|Equivalente a **putc**, pero implementado solo como una función, en lugar de como una función y una macro.|
|**fputwc**|Versión con caracteres anchos de **fputc**. Escribe *c* como un carácter multibyte o carácter ancho en función de si *flujo* se abre en modo de texto o binario.|

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados a la consola:**stdin**, **stdout**, y **stderr**: se deben redirigir antes funciones de tiempo de ejecución de C puedan usarlos en las aplicaciones UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
