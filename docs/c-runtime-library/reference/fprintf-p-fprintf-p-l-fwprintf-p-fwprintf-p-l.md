---
title: _fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _fwprintf_p
- _fprintf_p_l
- _fwprintf_p_l
- _fprintf_p
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
apitype: DLLExport
f1_keywords:
- _fprintf_p
- _ftprintf_p
- fwprintf_p
- _fwprintf_p
- fprintf_p
- ftprintf_p
dev_langs:
- C++
helpviewer_keywords:
- fprintf_p_l function
- fprintf_p function
- _fprintf_p_l function
- _fprintf_p function
- _ftprintf_p_l function
- streams, printing formatted data to
- _fwprintf_p function
- fwprintf_p function
- _ftprintf_p function
- _fwprintf_p_l function
- ftprintf_p function
- printing [C++], formatted data to streams
- ftprintf_p_l function
- fwprintf_p_l function
ms.assetid: 46b082e1-45ba-4383-9ee4-97015aa50bc6
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 10191be9cc824c74fd1679738c2083d0c80f1310
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="fprintfp-fprintfpl-fwprintfp-fwprintfpl"></a>_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l

Imprime datos con formato en una secuencia.

## <a name="syntax"></a>Sintaxis

```C
int _fprintf_p(
   FILE *stream,
   const char *format [,
   argument ]...
);
int _fprintf_p_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument ]...
);
int _fwprintf_p(
   FILE *stream,
   const wchar_t *format [,
   argument ]...
);
int _fwprintf_p_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument ]...
);
```

### <a name="parameters"></a>Parámetros

*Secuencia*<br/>
Puntero a la estructura **FILE**.

*format*<br/>
Cadena de control de formato.

*Argumento*<br/>
Argumentos opcionales.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**_fprintf_p** y **_fwprintf_p** devuelto por el número de caracteres escrito o un valor negativo cuando se produce un error de salida.

## <a name="remarks"></a>Comentarios

**_fprintf_p** da formato e imprime una serie de caracteres y valores a la salida de *flujo*. Cada función *argumento* (si existe) se convierte y sale según la especificación de formato correspondiente de *formato*. Para **_fprintf_p**, *formato* argumento tiene la misma sintaxis y el uso que tiene en **_printf_p**. Estas funciones admiten parámetros de posición, lo que significa que se puede cambiar el orden de los parámetros usados por la cadena de formato. Para obtener más información sobre parámetros de posición, consulte [printf_p (Parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md).

**_fwprintf_p** es una versión con caracteres anchos de **_fprintf_p**; en **_fwprintf_p**, *formato* es una cadena de caracteres anchos. Estas funciones se comportan igual si el flujo se abre en modo ANSI. **_fprintf_p** no admite actualmente la salida en un flujo UNICODE.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario.

Al igual que las versiones no seguras (vea [fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)), estas funciones validan sus parámetros e invocar el controlador de parámetros no válidos, tal y como se describe en [devalidacióndeparámetros](../../c-runtime-library/parameter-validation.md), si el valor *flujo* o *formato* es un puntero nulo o si no hay ningún especificador de formato desconocido o con formato incorrecto. Si la ejecución puede continuar, las funciones devuelven -1 y establecen **errno** a **EINVAL**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_ftprintf_p**|**_fprintf_p**|**_fprintf_p**|**_fwprintf_p**|
|**_ftprintf_p_l**|**_fprintf_p_l**|**_fprintf_p_l**|**_fwprintf_p_l**|

Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**_fprintf_p**, **_fprintf_p_l**|\<stdio.h>|
|**_fwprintf_p**, **_fwprintf_p_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fprintf_p.c
// This program uses _fprintf_p to format various
// data and print it to the file named FPRINTF_P.OUT. It
// then displays FPRINTF_P.OUT on the screen using the system
// function to invoke the operating-system TYPE command.
//

#include <stdio.h>
#include <process.h>

int main( void )
{
    FILE    *stream = NULL;
    int     i = 10;
    double  fp = 1.5;
    char    s[] = "this is a string";
    char    c = '\n';

    // Open the file
    if ( fopen_s( &stream, "fprintf_p.out", "w" ) == 0)
    {
        // Format and print data
        _fprintf_p( stream, "%2$s%1$c", c, s );
        _fprintf_p( stream, "%d\n", i );
        _fprintf_p( stream, "%f\n", fp );

        // Close the file
        fclose( stream );
    }

    // Verify our data
    system( "type fprintf_p.out" );
}
```

```Output
this is a string
10
1.500000
```

## <a name="see-also"></a>Vea también

[E/S de secuencia](../../c-runtime-library/stream-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[printf_p (parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)<br/>
[_cprintf_s, _cprintf_s_l, _cwprintf_s, _cwprintf_s_l](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)<br/>
[printf_p (parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
