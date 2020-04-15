---
title: _fputchar, _fputwchar
ms.date: 4/2/2020
api_name:
- _fputchar
- _fputwchar
- _o__fputchar
- _o__fputwchar
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
- fputtchar
- _fputwchar
- fputwchar
- _fputtchar
- _fputchar
helpviewer_keywords:
- fputchar function
- standard output, writing to
- _fputtchar function
- fputwchar function
- _fputwchar function
- fputtchar function
- _fputchar function
ms.assetid: b92ff600-a924-4f2b-b0e7-3097ee31bdff
ms.openlocfilehash: 29d23dcaba75ad87b462a1a87c7a2ad9c8c7298b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346170"
---
# <a name="_fputchar-_fputwchar"></a>_fputchar, _fputwchar

Escribe un carácter en **stdout**.

## <a name="syntax"></a>Sintaxis

```C
int _fputchar(
   int c
);
wint_t _fputwchar(
   wchar_t c
);
```

### <a name="parameters"></a>Parámetros

*C*<br/>
Carácter que se va a escribir.

## <a name="return-value"></a>Valor devuelto

Cada una de estas funciones devuelve el carácter escrito. Por **_fputchar**, un valor devuelto de **EOF** indica un error. Por **_fputwchar**, un valor devuelto de **WEOF** indica un error. Si c es **NULL**, estas funciones generan una excepción de parámetro no válida, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, devuelven **EOF** (o **WEOF**) y establecen **errno** en **EINVAL**.

Para obtener más información sobre estos y otros códigos error, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Ambas funciones escriben el carácter único *c* en **stdout** y avanza el indicador según corresponda. **_fputchar** es `fputc( stdout )`equivalente a . También es equivalente a **putchar**, pero implementado sólo como una función, en lugar de como una función y una macro. A diferencia de **fputc** y **putchar,** estas funciones no son compatibles con el estándar ANSI.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_fputtchar**|**_fputchar**|**_fputchar**|**_fputwchar**|

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fputchar**|\<stdio.h>|
|**_fputwchar**|\<stdio.h> o \<wchar.h>|

La consola no se admite en aplicaciones de la Plataforma universal de Windows (UWP). Los identificadores de secuencia estándar asociados a la consola **(stdin,** **stdout**y **stderr)** deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fputchar.c
// This program uses _fputchar
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
    char strptr[] = "This is a test of _fputchar!!\n";
    char *p = NULL;

    // Print line to stream using _fputchar.
    p = strptr;
    while( (*p != '\0') && _fputchar( *(p++) ) != EOF )
      ;
}
```

```Output
This is a test of _fputchar!!
```

## <a name="see-also"></a>Consulte también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc, fgetwc](fgetc-fgetwc.md)<br/>
[putc, putwc](putc-putwc.md)<br/>
