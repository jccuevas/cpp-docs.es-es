---
title: strtoll, _strtoll_l, wcstoll, _wcstoll_l
ms.date: 11/04/2016
apiname:
- strtoll
- wcstoll
- _strtoll_l
- _wcstoll_l
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
- _strtoll_l
- _tcstoll_l
- _tcstoll
- _wcstoll_l
- strtoll
- wcstoll
helpviewer_keywords:
- _tcstoll_l function
- _wcstoll_l function
- strtoll function
- wcstoll function
- _tcstoll function
- _strtoll_l function
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
ms.openlocfilehash: 53ae4ab1d482478c50aa257acdc974569bfc05f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523183"
---
# <a name="strtoll-strtolll-wcstoll-wcstolll"></a>strtoll, _strtoll_l, wcstoll, _wcstoll_l

Convierte una cadena en un **largo** **largo** valor.

## <a name="syntax"></a>Sintaxis

```C
long long strtoll(
   const char *strSource,
   char **endptr,
   int base
);
long long wcstoll(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long long _strtoll_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long long _wcstoll_l(
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

**strtoll** devuelve el valor que se representa en la cadena de *strSource*, excepto cuando la representación produciría desbordamiento, en ese caso, devuelve **LLONG_MAX** o **LLONG_MIN**. La función devuelve 0 si no se puede efectuar ninguna conversión. **wcstoll** devuelve valores de manera parecida a **strtoll**.

**LLONG_MAX** y **LLONG_MIN** se definen en los límites. H.

Si *strSource* es **NULL** o *base* es distinto de cero y menor que 2 o mayor que 36, **errno** está establecido en **EINVAL** .

Para obtener más información sobre los códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

El **strtoll** función convierte *strSource* a un **largo** **largo**. Ambas funciones dejan de leer la cadena *strSource* en el primer carácter que no se reconocen como parte de un número. Esto puede ser el carácter nulo final, o puede ser el primer carácter numérico que es mayor o igual a *base*. **wcstoll** es una versión con caracteres anchos de **strtoll**; su *strSource* argumento es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoll**|**strtoll**|**strtoll**|**wcstoll**|
|**_tcstoll_l**|**_strtoll_l**|**_strtoll_l**|**_wcstoll_l**|

La configuración regional **LC_NUMERIC** valor de la categoría determina el reconocimiento del carácter base en *strSource*; para obtener más información, consulte [setlocale, _wsetlocale](setlocale-wsetlocale.md). Las funciones que no tienen la **_l** sufijo usar la configuración regional actual. **_strtoll_l** y **_wcstoll_l** son idénticas a las funciones correspondientes que no tienen el sufijo, salvo que usan la configuración regional que se pasa en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no **NULL**, un puntero al carácter que detuvo el análisis se almacena en la ubicación en la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontró ningún dígito válido o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación en la que apunta *endptr*.

**strtoll** espera *strSource* para que apunte a una cadena de la forma siguiente:

> [*espacio en blanco*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **X** }]] [*dígitos* &#124; *letras*]  

Un *espacio en blanco* puede constar de caracteres de espacio y tabulación, que se omiten; *dígitos* son uno o más dígitos decimales; *letras* son una o varias de las letras 'a' a 'z' (o 'A' a 'Z'). El primer carácter que no se ajusta a este formato detiene el análisis. Si *base* está entre 2 y 36, se puede usar como base del número. Si *base* es 0, los caracteres iniciales de la cadena que se apunta a *strSource* se usan para determinar la base. Si el primer carácter es «0» y el segundo carácter no es «x» ni «X», la cadena se interpreta como un entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la "a" a la "z" (o de la "A" a la "Z") se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que *base*. El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, si *base* es 0 y el primer carácter examinado es "0", se supone un entero octal y un carácter '8' o '9' detiene el análisis.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtoll**, **_strtoll_l**|\<stdlib.h>|
|**wcstoll**, **_wcstoll_l**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
