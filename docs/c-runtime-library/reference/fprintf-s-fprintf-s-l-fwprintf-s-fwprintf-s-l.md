---
title: fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l
ms.date: 11/04/2016
apiname:
- _fprintf_s_l
- fwprintf_s
- fprintf_s
- _fwprintf_s_l
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
- _ftprintf_s
- fprintf_s
- fwprintf_s
helpviewer_keywords:
- ftprintf_s_l function
- ftprintf_s function
- _fprintf_s_l function
- _ftprintf_s function
- _ftprintf_s_l function
- fwprintf_s_l function
- fwprintf_s function
- fprintf_s_l function
- fprintf_s function
- _fwprintf_s_l function
- print formatted data to streams
ms.assetid: 16067c3c-69ce-472a-8272-9aadf1f5beed
ms.openlocfilehash: 05886dc4ce7de771749f157913a222b6b01a5c5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62333162"
---
# <a name="fprintfs-fprintfsl-fwprintfs-fwprintfsl"></a>fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l

Imprima datos con formato en una secuencia. Se trata de versiones de [fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md) con mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
int fprintf_s(
   FILE *stream,
   const char *format [,
   argument_list ]
);
int _fprintf_s_l(
   FILE *stream,
   const char *format,
   locale_t locale [,
   argument_list ]
);
int fwprintf_s(
   FILE *stream,
   const wchar_t *format [,
   argument_list ]
);
int _fwprintf_s_l(
   FILE *stream,
   const wchar_t *format,
   locale_t locale [,
   argument_list ]
);
```

### <a name="parameters"></a>Parámetros

*stream*<br/>
Puntero a la estructura **FILE**.

*format*<br/>
Cadena de control de formato.

*argument_list*<br/>
Argumentos opcionales de la cadena de formato.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**fprintf_s** devuelve el número de bytes escritos. **fwprintf_s** devuelve el número de caracteres anchos escritos. Cada una de estas funciones devuelve un valor negativo cuando se produce un error de salida.

## <a name="remarks"></a>Comentarios

**fprintf_s** da formato e imprime una serie de caracteres y valores en la salida *secuencia*. Cada argumento de *argument_list* (si existe) se convierte y sale según la especificación de formato correspondiente de *formato*. El *formato* argumento usa el [dar formato a la sintaxis de especificación de funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

**fwprintf_s** es una versión con caracteres anchos de **fprintf_s**; en **fwprintf_s**, *formato* es una cadena de caracteres anchos. Estas funciones se comportan igual si el flujo se abre en modo ANSI. **fprintf_s** no admite actualmente la salida en un flujo UNICODE.

Las versiones de estas funciones con el **_l** sufijo son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.

> [!IMPORTANT]
> Asegúrese de que *format* no es una cadena definida por el usuario.

Como las versiones no seguras (vea [fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)), estas funciones validan sus parámetros e invocan el controlador de parámetros no válidos, tal y como se describe en [devalidacióndeparámetros](../../c-runtime-library/parameter-validation.md), si *secuencia* o *formato* es un puntero nulo. También se valida la propia cadena de formato. Si hay algún especificador de formato desconocido o con formato incorrecto, estas funciones generan la excepción de parámetro no válido. En todos los casos, si la ejecución puede continuar, las funciones devuelven -1 y establezca **errno** a **EINVAL**. Consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de error.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ftprintf_s**|**fprintf_s**|**fprintf_s**|**fwprintf_s**|
|**_ftprintf_s_l**|**_fprintf_s_l**|**_fprintf_s_l**|**_fwprintf_s_l**|

Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado necesario|
|--------------|---------------------|
|**fprintf_s**, **_fprintf_s_l**|\<stdio.h>|
|**fwprintf_s**, **_fwprintf_s_l**|\<stdio.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_fprintf_s.c
// This program uses fprintf_s to format various
// data and print it to the file named FPRINTF_S.OUT. It
// then displays FPRINTF_S.OUT on the screen using the system
// function to invoke the operating-system TYPE command.

#include <stdio.h>
#include <process.h>

FILE *stream;

int main( void )
{
   int    i = 10;
   double fp = 1.5;
   char   s[] = "this is a string";
   char   c = '\n';

   fopen_s( &stream, "fprintf_s.out", "w" );
   fprintf_s( stream, "%s%c", s, c );
   fprintf_s( stream, "%d\n", i );
   fprintf_s( stream, "%f\n", fp );
   fclose( stream );
   system( "type fprintf_s.out" );
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
