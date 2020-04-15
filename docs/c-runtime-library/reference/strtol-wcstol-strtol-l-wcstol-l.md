---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 4/2/2020
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- _o__strtol_l
- _o__wcstol_l
- _o_strtol
- _o_wcstol
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
- _wcstol_l
- strtol
- _tcstol
- wcstol
- _strtol_l
- _tcstol_l
helpviewer_keywords:
- wcstol function
- wcstol_l function
- _tcstol function
- string conversion, to integers
- tcstol function
- strtol_l function
- _wcstol_l function
- _strtol_l function
- strtol function
ms.assetid: 1787c96a-f283-4a83-9325-33cfc1c7e240
no-loc:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
- LONG_MAX
- LONG_MIN
- errno
- ERANGE
- EINVAL
- LC_NUMERIC
- _tcstol
- _tcstol_l
- localeconv
- setlocale
- _wsetlocale
- strtod
- _strtod_l
- wcstod
- _wcstod_l
- strtoll
- _strtoll_l
- wcstoll
- _wcstoll_l
- strtoul
- _strtoul_l
- wcstoul
- _wcstoul_l
- atof
- _atof_l
- _wtof
- _wtof_l
ms.openlocfilehash: dbeaf04d34aa20e15de48e99082ed07edb6129ab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320473"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Convierta cadenas en un valor entero **largo.**

## <a name="syntax"></a>Sintaxis

```C
long strtol(
   const char *string,
   char **end_ptr,
   int base
);
long wcstol(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base
);
long _strtol_l(
   const char *string,
   char **end_ptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
   const wchar_t *string,
   wchar_t **end_ptr,
   int base,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*Cadena*\
Cadena terminada en NULL que se va a convertir.

*end_ptr*\
Un parámetro de salida, establecido para que apunte al carácter después del último carácter interpretado. Se omite, si **NULL**.

*Base*\
Base numérica que se va a usar.

*Configuración regional*\
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strtol**, **wcstol**, **_strtol_l**y **_wcstol_l** devolver el valor representado en *string*. Devuelven 0 si no es posible realizar ninguna conversión. Cuando la representación provocaría un desbordamiento, devuelven **LONG_MAX** o **LONG_MIN**.

**errno** se establece en **ERANGE** si se produce un desbordamiento o subdesbordamiento. Se establece en **EINVAL** si *string* es **NULL**. O bien, si *la base* es distinta de cero y menor que 2, o mayor que 36. Para obtener más información sobre **ERANGE**, **EINVAL**y otros códigos de retorno, consulte [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Las **funciones strtol**, **wcstol**, **_strtol_l**y **_wcstol_l** convierten la *cadena* en un **valor largo.** Dejan de leer *la cadena* en el primer carácter no reconocido como parte de un número. Puede ser el carácter nulo de terminación, o el primer carácter alfanumérico mayor o igual que *base*.

**wcstol** y **_wcstol_l** son versiones de caracteres anchos de **strtol** y **_strtol_l**. Su argumento *string* es una cadena de caracteres anchos. Estas funciones se comportan de forma idéntica a **strtol** y **_strtol_l** de lo contrario. La configuración de **categoría de LC_NUMERIC** de la configuración regional determina el reconocimiento del carácter de radio (el marcador fraccionario o el punto decimal) en la *cadena*. Las funciones **strtol** y **wcstol** utilizan la configuración regional actual. **_strtol_l** y **_wcstol_l** usar la configuración regional pasada en su lugar. Para obtener más información, consulte [setlocale] y [Locale](../../c-runtime-library/locale.md).

Cuando *end_ptr* es **NULL**, se omite. De lo contrario, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *end_ptr*. No es posible realizar ninguna conversión si no se encuentra ningún dígito válido o si se especifica una base no válida. A continuación, el valor de *string* se almacena en la ubicación a la que apunta *end_ptr*.

**strtol** espera *string* que string apunte a una cadena de la siguiente forma:

> [*espacio en blanco*] **-**[&#124;]**+** [**0** [x **x** &#124; **X** ]] [*alfanuméricos*]

Los corchetes`[ ]`( ) rodean elementos opcionales. Llaves rizadas y una`{ | }`barra vertical ( ) rodean alternativas para un solo elemento. *espacios en blanco* pueden constar de caracteres de espacio y tabulación, que se omiten. *los alfanuméricos* son dígitos decimales o las letras 'a' a 'z' (o 'A' a 'Z'). El primer carácter que no se ajusta a esta forma detiene el análisis. Si *la base* está entre 2 y 36, entonces se utiliza como la base del número. Si *base* es 0, los caracteres iniciales de la cadena señalada por *cadena* se utilizan para determinar la base. Si el primer carácter es 0 y el segundo carácter no es 'x' o 'X', la cadena se interpreta como un entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras 'a' a 'z' (o 'A' a 'Z') se les asignan los valores 10 a 35. El análisis solo permite letras cuyos valores son menores que *la base.* El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, supongamos que *la cadena* comienza con "01". Si *base* es 0, el analizador asume que es un entero octal. Un carácter '8' o '9' detiene el escaneo.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> o \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|
|**_wcstol_l**|\<stdlib.h> o \<wchar.h>|

Las **_strtol_l** **_wcstol_l** funciones y son específicas de Microsoft, no parte de la biblioteca Estándar de C. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../compatibility.md).

## <a name="example"></a>Ejemplo

Vea el [strtod](strtod-strtod-l-wcstod-wcstod-l.md)ejemplo de .

## <a name="see-also"></a>Consulte también

[Conversión de datos](../data-conversion.md)\
[Configuración regional](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Funciones de valor numérico de cadena a número](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
