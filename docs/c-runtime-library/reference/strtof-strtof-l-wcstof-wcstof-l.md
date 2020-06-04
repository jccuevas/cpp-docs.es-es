---
title: strtof, _strtof_l, wcstof, _wcstof_l
ms.date: 4/2/2020
api_name:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
- _o__strtof_l
- _o__wcstof_l
- _o_strtof
- _o_wcstof
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
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
ms.openlocfilehash: a7ff3a8eaa3d9d42a5f1a9a7bf277a847aeccfee
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910867"
---
# <a name="strtof-_strtof_l-wcstof-_wcstof_l"></a>strtof, _strtof_l, wcstof, _wcstof_l

Convierte las cadenas en un valor de punto flotante de precisión sencilla.

## <a name="syntax"></a>Sintaxis

```C
float strtof(
   const char *strSource,
   char **endptr
);
float _strtof_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
float wcstof(
   const wchar_t *strSource,
   wchar_t **endptr
);
float wcstof_l(
   const wchar_t *strSource,
   wchar_t **endptr,
   _locale_t locale
);
```

## <a name="parameters"></a>Parámetros

*strSource*<br/>
Cadena terminada en NULL que se va a convertir.

*endptr*<br/>
Puntero al carácter que detiene el examen.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

**strtof** devuelve el valor del número de punto flotante, excepto cuando la representación provocaría un desbordamiento, en cuyo caso la función devuelve +/-**HUGE_VALF**. El signo de **HUGE_VALF** coincide con el signo del valor que no se puede representar. **strtof** devuelve 0 si no se puede realizar ninguna conversión o si se produce un subdesbordamiento.

**wcstof** devuelve valores de forma análoga a **strtof**. En ambas funciones, **errno** se establece en **ERANGE** si se produce desbordamiento o subdesbordamiento y se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md).

Para obtener más información sobre los códigos de retorno, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Observaciones

Cada función convierte la cadena de entrada *strSource* en un valor **float**. La función **strtof** convierte *strSource* en un valor de precisión sencilla. **strtof** deja de leer la cadena *strSource* en el primer carácter que no reconoce como parte de un número. Este puede ser el carácter nulo de terminación. **wcstof** es una versión con caracteres anchos de **strtof**; su argumento *strSource* es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstof**|**strtof**|**strtof**|**wcstof**|
|**_tcstof_l**|**_strtof_l**|**_strtof_l**|**_wcstof_l**|

La configuración de la categoría **LC_NUMERIC** de la configuración regional actual determina el reconocimiento del carácter de base en *strSource*; para obtener más información, vea [setlocale, _wsetlocale](setlocale-wsetlocale.md). Las funciones que no tienen el sufijo **_L** usan la configuración regional actual; las que tienen el sufijo son idénticas, salvo que usan la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no es **null**, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontraron dígitos válidos o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación a la que apunta *endptr*.

**strtof** espera que *strSource* señale a una cadena con el formato siguiente:

[*espacio en blanco*] [*signo*] [*dígitos*] [__.__ *dígitos*] [{**e** &#124; **e**} [*signo*] *dígitos*]

Un espacio en *blanco* puede constar de caracteres de espacio y tabulación, que se omiten; el *signo* es más (**+**) o menos (**-**); y los *dígitos* son uno o más dígitos decimales. Si no aparece ningún dígito antes del carácter de base, debe aparecer al menos uno después del carácter de base. Los dígitos decimales pueden ir seguidos de un exponente, que consta de una letra de presentación (**e** o **e**) y un entero con signo opcional. Si no aparece ni una parte exponencial ni un carácter de base, se supone que un carácter de base sigue al último dígito de la cadena. El primer carácter que no se ajusta a este formato detiene el análisis.

Las versiones de UCRT de estas funciones no admiten la conversión de Letras de exponente de estilo Fortran (**d** o **d**). Esta extensión no estándar era compatible con versiones anteriores de CRT y puede que sea un cambio decisivo para el código.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtof**, **_strtof_l**|C: \<stdlib.h> C++: &lt;cstdlib> o \<stdlib.h>|
|**wcstof**, **_wcstof_l**|C: \<stdlib.h> o \<wchar.h> C++: &lt;cstdlib>, \<stdlib.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strtof.c
// This program uses strtof to convert a
// string to a single-precision value.

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char *string;
   char *stopstring;
   float x;

   string = "3.14159This stopped it";
   x = strtof(string, &stopstring);
   printf("string = %s\n", string);
   printf("   strtof = %f\n", x);
   printf("   Stopped scan at: %s\n\n", stopstring);
}
```

```Output
string = 3.14159This stopped it
   strtof = 3.141590
   Stopped scan at: This stopped it
```

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtod, _strtod_l, wcstod, _wcstod_l](strtod-strtod-l-wcstod-wcstod-l.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
