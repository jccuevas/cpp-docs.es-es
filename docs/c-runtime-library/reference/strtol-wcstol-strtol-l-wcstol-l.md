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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: cc54884cd32ffa9118abfb6d46d659125a44262c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912647"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Convierte cadenas en un valor entero **largo** .

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

*String@*\
Cadena terminada en NULL que se va a convertir.

*end_ptr*\
Un parámetro de salida, establecido para que apunte al carácter situado después del último carácter interpretado. Se omite si **es null**.

*básica*\
Base numérica que se va a usar.

*configuración regional*\
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strtol**, **wcstol**, **_strtol_l**y **_wcstol_l** devuelven el valor representado en *String*. Devuelven 0 si no es posible realizar ninguna conversión. Cuando la representación provocaría un desbordamiento, devolverán **LONG_MAX** o **LONG_MIN**.

**errno** se establece en **ERANGE** si se produce desbordamiento o subdesbordamiento. Se establece en **EINVAL** si *String* es **null**. O bien, si *base* es distinto de cero y menor que 2 o mayor que 36. Para obtener más información sobre **ERANGE**, **EINVAL**y otros códigos de retorno, vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Las funciones **strtol**, **wcstol**, **_strtol_l**y **_wcstol_l** convierten la *cadena* en un **valor Long**. Dejan de leer la *cadena* en el primer carácter que no se reconoce como parte de un número. Puede ser el carácter de terminación null o el primer carácter alfanumérico mayor o igual que *base*.

**wcstol** y **_wcstol_l** son versiones con caracteres anchos de **strtol** y **_strtol_l**. Su argumento de *cadena* es una cadena de caracteres anchos. Estas funciones se comportan de manera idéntica a **strtol** y **_strtol_l** en caso contrario. La configuración de la categoría **LC_NUMERIC** de la configuración regional determina el reconocimiento del carácter de base (el marcador fraccionario o el separador decimal) en la *cadena*. Las funciones **strtol** y **wcstol** usan la configuración regional actual. **_strtol_l** y **_wcstol_l** usan en su lugar la configuración regional que se pasa. Para obtener más información, vea [setlocale] y [configuración regional](../../c-runtime-library/locale.md).

Cuando *end_ptr* es **null**, se omite. De lo contrario, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que señala *end_ptr*. No es posible realizar ninguna conversión si no se encuentran dígitos válidos o se ha especificado una base no válida. Después, el valor de *cadena* se almacena en la ubicación a la que apunta *end_ptr*.

**strtol** espera que la *cadena* señale a una cadena con el formato siguiente:

> [*espacio en blanco*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **x** }]] [*alfanuméricos*]

Los corchetes`[ ]`() rodean los elementos opcionales. Las llaves y las alternativas de barra vertical`{ | }`() para un único elemento. los *espacios en blanco* pueden constar de caracteres de espacio y tabulación, que se omiten. los *caracteres alfanuméricos* son dígitos decimales o las letras de la ' a ' a la ' z ' (o de la ' a ' a la ' z '). El primer carácter que no se ajusta a este formulario detiene el examen. Si *base* se encuentra entre 2 y 36, se usa como base del número. Si *base* es 0, los caracteres iniciales de la cadena a la que apunta la *cadena* se usan para determinar la base. Si el primer carácter es 0 y el segundo carácter no es ' x ' ni ' X ', la cadena se interpreta como un entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la ' a ' a la ' z ' (o de la ' a ' a la ' Z ') se les asignan los valores del 10 al 35. El examen solo permite Letras cuyos valores son menores que *base*. El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, supongamos que la *cadena* comienza con "01". Si *base* es 0, el analizador supone que es un entero octal. Un carácter "8" o "9" detiene el examen.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

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

Las **_strtol_l** funciones **_wcstol_l** y son específicas de Microsoft, no forman parte de la biblioteca estándar de C. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Consulta también

[Conversión de datos](../data-conversion.md)\
[Configuración regional](../locale.md)\
[localeconv](localeconv.md)\
[setlocale, _wsetlocale](setlocale-wsetlocale.md)\
[Funciones de cadena en valores numéricos](../string-to-numeric-value-functions.md)\
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)\
[strtoll, _strtoll_l, wcstoll, _wcstoll_l](strtoll-strtoll-l-wcstoll-wcstoll-l.md)\
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)\
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)
