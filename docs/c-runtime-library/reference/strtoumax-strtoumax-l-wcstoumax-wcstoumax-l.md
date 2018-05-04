---
title: strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcstoumax_l
- _strtoumax_l
- wcstoumax
- strtoumax
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcstoumax
- _tcstoumax
- _strtoumax_l
- _wcstoumax_l
- _tcstoumax_l
- strtoumax
dev_langs:
- C++
helpviewer_keywords:
- _strtoumax_l function
- conversion functions
- wcstoumax function
- _wcstoumax_l function
- strtoumax function
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0691e26387f70e80718d8af84ba9ff18ad7fd489
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="strtoumax-strtoumaxl-wcstoumax-wcstoumaxl"></a>strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l

Convierte las cadenas en un valor entero del tipo de entero sin signo compatible más grande.

## <a name="syntax"></a>Sintaxis

```C
uintmax_t strtoumax(
   const char *strSource,
   char **endptr,
   int base
);
uintmax_t _strtoumax_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
uintmax_t wcstoumax(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
uintmax_t _wcstoumax_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*strSource*<br/>
Cadena terminada en NULL que se va a convertir.

*endptr*<br/>
Puntero al carácter que detiene el examen.

*base*<br/>
Base numérica que se va a usar.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strtoumax** devuelve el valor convertido, si hay alguno, o **UINTMAX_MAX** si se produce desbordamiento. **strtoumax** devuelve 0 si no se puede realizar ninguna conversión. **wcstoumax** devuelve valores de manera parecida a **strtoumax**. Para ambas funciones, **errno** está establecido en **ERANGE** si se produce desbordamiento o subdesbordamiento.

Para obtener más información sobre los códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cada una de estas funciones convierte la cadena de entrada *strSource* a una **uintmax_t** valor entero.

**strtoumax** deja de leer la cadena *strSource* en el primer carácter que no se reconoce como parte de un número. Puede tratarse del carácter nulo final, o puede ser el primer carácter numérico que es mayor o igual que *base*. El **LC_NUMERIC** valor de la categoría de la configuración regional determina el reconocimiento del carácter base en *strSource*. Para obtener más información, vea [setlocale, _wsetlocale](setlocale-wsetlocale.md). **strtoumax** y **wcstoumax** usan la configuración regional actual; **_strtoumax_l** y **_wcstoumax_l** son idénticas salvo que usan la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no **NULL**, un puntero al carácter que detuvo el análisis se almacena en la ubicación que apunta a *endptr*. Si no se puede realizar ninguna conversión (no válidos se encontraron dígitos o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación que apunta a *endptr*.

La versión con caracteres anchos de **strtoumax** es **wcstoumax**; su *strSource* argumento es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoumax**|**strtoumax**|**strtoumax**|**wcstoumax**|
|**_tcstoumax_l**|**strtoumax_l**|**_strtoumax_l**|**_wcstoumax_l**|

**strtoumax** espera *strSource* para que apunte a una cadena de la forma siguiente:

> [*espacio en blanco*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*dígitos* &#124; *letras*]  

A *espacio en blanco* puede constar de caracteres de espacio y tabulación, que se omiten. *dígitos* son uno o más dígitos decimales. *letras* son una o varias de las letras "a" a "z" (o 'A' a la 'Z'). El primer carácter que no se ajusta a este formato detiene el análisis. Si *base* está entre 2 y 36, se usa como base del número. Si *base* es 0, los caracteres iniciales de la cadena que apunta a *strSource* se utilizan para determinar la base. Si el primer carácter es «0» y el segundo carácter no es «x» ni «X», la cadena se interpreta como un entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la "a" a la "z" (o de la "A" a la "Z") se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que *base*. El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, si *base* es 0 y el primer carácter que se examinan es '0', se supone un entero octal y un carácter '8' o '9' debería detener la búsqueda. **strtoumax** permite un signo más (**+**) o un signo (**-**) prefijo; inicial signo indica que el valor devuelto es el complemento de dos de los valor absoluto de la cadena convertida.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtoumax**|\<stdlib.h>|
|**wcstoumax**|\<stdlib.h> o \<wchar.h>|
|**_strtoumax_l**|\<stdlib.h>|
|**_wcstoumax_l**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtoimax, _strtoimax_l, wcstoimax, _wcstoimax_l](strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
