---
title: strtoul, _strtoul_l, wcstoul, _wcstoul_l
ms.date: 4/2/2020
api_name:
- _wcstoul_l
- _strtoul_l
- strtoul
- wcstoul
- _o__strtoul_l
- _o__wcstoul_l
- _o_strtoul
- _o_wcstoul
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
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strtoul
- _tcstoul
- wcstoul
helpviewer_keywords:
- _wcstoul_l function
- _tcstoul function
- _strtoul_l function
- string conversion, to integers
- wcstoul function
- strtoul function
- wcstoul_l function
- strtoul_l function
- tcstoul function
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
ms.openlocfilehash: 9e0e466893aedb565fcd5852c6768ecfc620c611
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912404"
---
# <a name="strtoul-_strtoul_l-wcstoul-_wcstoul_l"></a>strtoul, _strtoul_l, wcstoul, _wcstoul_l

Convierte cadenas en un valor entero largo sin signo.

## <a name="syntax"></a>Sintaxis

```C
unsigned long strtoul(
   const char *strSource,
   char **endptr,
   int base
);
unsigned long _strtoul_l(
   const char *strSource,
   char **endptr,
   int base,
   _locale_t locale
);
unsigned long wcstoul(
   const wchar_t *strSource,
   wchar_t **endptr,
   int base
);
unsigned long _wcstoul_l(
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

**strtoul** devuelve el valor convertido, si existe, o **ULONG_MAX** en caso de desbordamiento. **strtoul** devuelve 0 si no se puede realizar ninguna conversión. **wcstoul** devuelve valores de forma análoga a **strtoul**. En ambas funciones, **errno** se establece en **ERANGE** si se produce desbordamiento o subdesbordamiento.

Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

Cada una de estas funciones convierte la cadena de entrada *strSource* en un **valor Long** **sin signo** .

**strtoul** deja de leer la cadena *strSource* en el primer carácter que no reconoce como parte de un número. Puede tratarse del carácter nulo final o puede ser el primer carácter numérico mayor o igual que *base*. La configuración de la categoría **LC_NUMERIC** de la configuración regional determina el reconocimiento del carácter de base en *strSource*; para obtener más información, vea [setlocale](setlocale-wsetlocale.md). **strtoul** y **wcstoul** usan la configuración regional actual; **_strtoul_l** y **_wcstoul_l** son idénticos, salvo que usan en su lugar la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no es **null**, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontraron dígitos válidos o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación a la que apunta *endptr*.

**wcstoul** es una versión con caracteres anchos de **strtoul**; su argumento *strSource* es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstoul**|**strtoul**|**strtoul**|**wcstoul**|
|**_tcstoul_l**|**strtoul_l**|**_strtoul_l**|**_wcstoul_l**|

**strtoul** espera que *strSource* señale a una cadena con el formato siguiente:

> [*espacio en blanco*] [{**+** &#124; **-**}] [**0** [{ **x** &#124; **x** }]] [*dígitos* &#124; *Letras*]

Un espacio en *blanco* puede constar de caracteres de espacio y tabulación, que se omiten. los *dígitos* son uno o más dígitos decimales. las *Letras* son una o varias letras de la ' a ' a la ' z ' (o de la ' a ' a la ' z '). El primer carácter que no se ajusta a este formato detiene el análisis. Si *base* se encuentra entre 2 y 36, se utiliza como base del número. Si *base* es 0, los caracteres iniciales de la cadena a la que apunta *strSource* se usan para determinar la base. Si el primer carácter es 0 y el segundo carácter no es 'x' ni 'X', la cadena se interpreta como entero octal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la "a" a la "z" (o de la "A" a la "Z") se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que *base*. El primer carácter que está fuera del intervalo de la base detiene el análisis. Por ejemplo, si *base* es 0 y el primer carácter examinado es "0", se supone un entero octal y un carácter "8" o "9" detendrá el examen. **strtoul** permite un prefijo**+** de signo más (**-**) o menos (); un signo menos inicial indica que el valor devuelto es negado.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtoul**|\<stdlib.h>|
|**wcstoul**|\<stdlib.h> o \<wchar.h>|
|**_strtoul_l**|\<stdlib.h>|
|**_wcstoul_l**|\<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Vea el ejemplo de [strtod](strtod-strtod-l-wcstod-wcstod-l.md).

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
