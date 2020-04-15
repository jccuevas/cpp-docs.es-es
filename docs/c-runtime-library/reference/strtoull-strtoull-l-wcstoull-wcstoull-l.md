---
title: strtoull, _strtoull_l, wcstoull, _wcstoull_l
ms.date: 4/2/2020
api_name:
- _strtoull_l
- _wcstoull_l
- strtoull
- wcstoull
- _o__strtoull_l
- _o__wcstoull_l
- _o_strtoull
- _o_wcstoull
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wcstoull_l
- _tcstoull
- _tcstoull_l
- wcstoull
- _strtoull_l
- strtoull
helpviewer_keywords:
- strtoull function
- _tcstoull_l function
- _tcstoull function
- _wcstoull_l function
- _strtoull_l function
- wcstoull function
ms.assetid: 36dac1cc-e901-40a0-8802-63562d6d01df
ms.openlocfilehash: 5a27218b9d83314f995df30fbe21d97031d371af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354057"
---
# <a name="strtoull-_strtoull_l-wcstoull-_wcstoull_l"></a>strtoull, _strtoull_l, wcstoull, _wcstoull_l

Convierte las cadenas en un valor largo de entero largo sin signo.

## <a name="syntax"></a>Sintaxis

```C
unsigned long long strtoull(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long long _strtoull_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long long wcstoull(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long long _wcstoull_l(
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

**strtoull** devuelve el valor convertido, si existe, o **ULLONG_MAX** en el desbordamiento. **strtoull** devuelve 0 si no se puede realizar ninguna conversión. **wcstoull** devuelve valores de forma análoga a **strtoull**. Para ambas funciones, **errno** se establece en **ERANGE** si se produce un desbordamiento o subdesbordamiento.

Para obtener más información sobre los códigos de retorno, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Cada una de estas funciones convierte la cadena de entrada *strSource* en un valor entero **largo** **sin** **signo.**

**strtoull** deja de leer la cadena *strSource* en el primer carácter que no puede reconocer como parte de un número. Puede ser el carácter nulo de terminación, o puede ser el primer carácter numérico que es mayor o igual que *base*. La configuración de la **categoría LC_NUMERIC** de la configuración regional determina el reconocimiento del carácter de radio en *strSource*; Para obtener más información, consulte [setlocale, _wsetlocale](setlocale-wsetlocale.md). **strtoull** y **wcstoull** utilizan la configuración regional actual; **_strtoull_l** y **_wcstoull_l** usar en su lugar la configuración regional que se pasa, pero que son idénticas de lo contrario. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no es **NULL**, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontró ningún dígito válido o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación a la que apunta *endptr*.

**wcstoull** es una versión de caracteres anchos de **strtoull** y su argumento *strSource* es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoull**|**strtoull**|**strtoull**|**wcstoull**|
|**_tcstoull_l**|**strtoull_l**|**_strtoull_l**|**_wcstoull_l**|

**strtoull** espera que *strSource* apunte a una cadena de la siguiente forma:

> [*espacio en blanco*] **-**[&#124;]**+** [**0** [x **x** &#124; **X** ]] [*dígitos* &#124; *letras*]

Un *espacio en blanco* puede constar de caracteres de espacio y tabulación, que se omiten. *dígitos* son uno o más dígitos decimales. *letras* son una o más de las letras 'a' a 'z' (o 'A' a 'Z'). El primer carácter que no se ajusta a este formato detiene el análisis. Si *la base* está entre 2 y 36, entonces se utiliza como la base del número. Si *base* es 0, los caracteres iniciales de la cadena a la que apunta *strSource* se utilizan para determinar la base. Si el primer carácter es «0» y el segundo carácter no es «x» ni «X», la cadena se interpreta como un entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la "a" a la "z" (o de la "A" a la "Z") se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que *base*. El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, si *base* es 0 y el primer carácter escaneado es '0', se asume un entero octal y un carácter '8' o '9' detiene el análisis. **strtoull** permite un**+** signo más (**-**) o un signo menos ( ) prefijo; un signo menos inicial indica que el valor devuelto está negado.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtoull**|\<stdlib.h>|
|**wcstoull**|\<stdlib.h> o \<wchar.h>|
|**_strtoull_l**|\<stdlib.h>|
|**_wcstoull_l**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
