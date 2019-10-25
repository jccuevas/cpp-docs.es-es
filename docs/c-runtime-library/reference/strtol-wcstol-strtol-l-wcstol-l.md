---
title: strtol, wcstol, _strtol_l, _wcstol_l
ms.date: 11/04/2016
api_name:
- strtol
- wcstol
- _strtol_l
- _wcstol_l
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
ms.openlocfilehash: b40362e93a41730e46ad0911b5a633118d024e9c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957639"
---
# <a name="strtol-wcstol-_strtol_l-_wcstol_l"></a>strtol, wcstol, _strtol_l, _wcstol_l

Convierte cadenas en un valor entero largo sin signo.

## <a name="syntax"></a>Sintaxis

```C
long strtol(
   const char *strSource,
   char **endptr,
   int base
);
long wcstol(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
long _strtol_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
long _wcstol_l(
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

**strtol** devuelve el valor representado en la cadena *strSource*, excepto cuando la representación provocaría un desbordamiento, en cuyo caso devuelve **LONG_MAX** o **LONG_MIN**. **strtol** devuelve 0 si no se puede realizar ninguna conversión. **wcstol** devuelve valores de forma análoga a **strtol**. En ambas funciones, **errno** se establece en **ERANGE** si se produce desbordamiento o subdesbordamiento.

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

La función **strtol** convierte *strSource* en **Long**. **strtol** deja de leer la cadena *strSource* en el primer carácter que no reconoce como parte de un número. Puede tratarse del carácter nulo final o puede ser el primer carácter numérico mayor o igual que *base*.

**wcstol** es una versión con caracteres anchos de **strtol**; su argumento *strSource* es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstol**|**strtol**|**strtol**|**wcstol**|
|**_tcstol_l**|**_strtol_l**|**_strtol_l**|**_wcstol_l**|

La configuración de la categoría **LC_NUMERIC** de la configuración regional actual determina el reconocimiento del carácter de base en *strSource*; para obtener más información, vea [setlocale](setlocale-wsetlocale.md). Las funciones sin el sufijo **_L** usan la configuración regional actual; **_strtol_l** y **_wcstol_l** son idénticos a las funciones correspondientes sin el sufijo **_L** , salvo que usan la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no es **null**, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontraron dígitos válidos o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación a la que apunta *endptr*.

**strtol** espera que *strSource* señale a una cadena con el formato siguiente:

> [*espacio en blanco*] [{ **+** &#124; &#124; &#124; }] [0 [{x x}]] [Letras de dígitos] **-**

Un espacio en *blanco* puede constar de caracteres de espacio y tabulación, que se omiten; los *dígitos* son uno o más dígitos decimales; las *Letras* son una o varias letras de la ' a ' a la ' z ' (o de la ' a ' a la ' z ').  El primer carácter que no se ajusta a este formato detiene el análisis. Si *base* se encuentra entre 2 y 36, se utiliza como base del número. Si *base* es 0, los caracteres iniciales de la cadena a la que apunta *strSource* se usan para determinar la base. Si el primer carácter es 0 y el segundo carácter no es 'x' ni 'X', la cadena se interpreta como entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la "a" a la "z" (o de la "A" a la "Z") se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que *base*. El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, si *base* es 0 y el primer carácter examinado es "0", se supone un entero octal y un carácter "8" o "9" detendrá el examen.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtol**|\<stdlib.h>|
|**wcstol**|\<stdlib.h> o \<wchar.h>|
|**_strtol_l**|\<stdlib.h>|

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
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
