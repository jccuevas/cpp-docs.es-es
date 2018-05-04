---
title: strtold, _strtold_l, wcstold, _wcstold_l | Microsoft Docs
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- wcstold
- strtold
- _strtold_l
- _wcstold_l
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
- _tcstold_l
- _wcstold_l
- _tcstold
- strtold
- _strtold_l
- wcstold
dev_langs:
- C++
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a5018f9245da77fbadb301a8fa45d1f0f7b4117
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="strtold-strtoldl-wcstold-wcstoldl"></a>strtold, _strtold_l, wcstold, _wcstold_l

Convierte las cadenas en un valor largo de punto flotante de precisión doble.

## <a name="syntax"></a>Sintaxis

```C
long double strtold(
   const char *strSource,
   char **endptr
);
long double _strtold_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
long double wcstold(
   const wchar_t *strSource,
   wchar_t **endptr
);
long double wcstold_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*strSource*<br/>
Cadena terminada en NULL que se va a convertir.

*endptr*<br/>
Puntero al carácter que detiene el examen.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strtold** devuelve el valor del número de punto flotante como un **largo** **doble**, excepto cuando la representación produciría desbordamiento, en ese caso, la función devuelve +/-**HUGE_VALL**. El inicio de sesión de **HUGE_VALL** coincide con el signo del valor que no se puede representar. **strtold** devuelve 0 si se puede realizar ninguna conversión o se produce un subdesbordamiento.

**wcstold** devuelve valores de manera parecida a **strtold**. Para ambas funciones, **errno** está establecido en **ERANGE** si se produce desbordamiento o subdesbordamiento y se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Para obtener más información sobre los códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

Cada función convierte la cadena de entrada *strSource* a una **largo** **doble**. El **strtold** función deja de leer la cadena *strSource* en el primer carácter que no se reconoce como parte de un número. Este puede ser el carácter nulo de terminación. La versión con caracteres anchos de **strtold** es **wcstold**; su *strSource* argumento es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstold**|**strtold**|**strtold**|**wcstold**|
|**_tcstold_l**|**_strtold_l**|**_strtold_l**|**_wcstold_l**|

El **LC_NUMERIC** valor de la categoría de la configuración regional actual determina el reconocimiento del carácter base en *strSource*. Para obtener más información, vea [setlocale, _wsetlocale](setlocale-wsetlocale.md). Las funciones sin el **_l** sufijo usar la configuración regional actual; **_strtold_l** y **_wcstold_l** son idénticas a **_strtold** y **_wcstold** salvo que usan en su lugar la configuración regional que pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no **NULL**, un puntero al carácter que detuvo el análisis se almacena en la ubicación que apunta a *endptr*. Si no se puede realizar ninguna conversión (no válidos se encontraron dígitos o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación que apunta a *endptr*.

**strtold** espera *strSource* para que apunte a una cadena de la forma siguiente:

[*espacio en blanco*] [*inicio de sesión*] [*dígitos*] [. *dígitos*] [{**d.** &#124; **d.** &#124; **e** &#124; **E**} [*inicio de sesión* ]*dígitos*]

A *espacio en blanco* puede constar de caracteres de espacio y tabulación, que se omiten; *inicio de sesión* sea más (**+**) o un signo menos (**-**); y *dígitos* son uno o más dígitos decimales. Si no aparece ningún dígito antes del carácter de base, debe aparecer al menos uno después del carácter de base. Los dígitos decimales pueden ir seguidos de un exponente, que consta de una letra inicial (**d**, **D**, **e** o **E**) y un entero con signo optativo. Si no aparece ni una parte exponencial ni un carácter de base, se supone que un carácter de base sigue al último dígito de la cadena. El primer carácter que no se ajusta a este formato detiene el análisis.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtold**, **_strtold_l**|\<stdlib.h>|
|**wcstold**, **_wcstold_l**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strtold.c
// Build with: cl /W4 /Tc crt_strtold.c
// This program uses strtold to convert a
// string to a long double-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   long double x;

   string = "3.1415926535898This stopped it";
   x = strtold(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtold = %.13Lf\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.1415926535898This stopped it
   strtold = 3.1415926535898
   Stopped scan at: This stopped it

```

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
