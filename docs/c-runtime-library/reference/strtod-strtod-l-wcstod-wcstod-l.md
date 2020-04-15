---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 4/2/2020
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
- _o__strtod_l
- _o__wcstod_l
- _o_strtod
- _o_wcstod
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
- _tcstod
- strtod
- wcstod
- _strtod_l
- _wcstod_l
- stdlib/strtod
- corecrt_wstdlib/wcstod
- stdlib/_strtod_l
- corecrt_wstdlib/_wcstod_l
helpviewer_keywords:
- wcstod_l function
- tcstod_l function
- _tcstod_l function
- strtod function
- _wcstod_l function
- wcstod function
- strtod_l function
- tcstod function
- _tcstod function
- _strtod_l function
- string conversion, to floating point values
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
ms.openlocfilehash: a688846d5db4d508327745728f8933c91bfd54e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337663"
---
# <a name="strtod-_strtod_l-wcstod-_wcstod_l"></a>strtod, _strtod_l, wcstod, _wcstod_l

Convierte las cadenas en un valor de precisión doble.

## <a name="syntax"></a>Sintaxis

```C
double strtod(
   const char *strSource,
   char **endptr
);
double _strtod_l(
   const char *strSource,
   char **endptr,
   _locale_t locale
);
double wcstod(
   const wchar_t *strSource,
   wchar_t **endptr
);
double wcstod_l(
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

**strtod** devuelve el valor del número de punto flotante, excepto cuando la representación provocaría un desbordamiento, en cuyo caso la función devuelve +/-**HUGE_VAL**. El signo de **HUGE_VAL** coincide con el signo del valor que no se puede representar. **strtod** devuelve 0 si no se puede realizar ninguna conversión o se produce un subdesbordamiento.

**wcstod** devuelve valores de forma análoga a **strtod**. Para ambas funciones, **errno** se establece en **ERANGE** si se produce un desbordamiento o subdesbordamiento y se invoca el controlador de parámetros no válidos, como se describe en Validación de [parámetros](../../c-runtime-library/parameter-validation.md). Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.

## <a name="remarks"></a>Observaciones

Cada función convierte la cadena de entrada *strSource* en un **doble**. La función **strtod** convierte *strSource* en un valor de precisión doble. **strtod** deja de leer la cadena *strSource* en el primer carácter que no puede reconocer como parte de un número. Este puede ser el carácter nulo de terminación. **wcstod** es una versión de caracteres anchos de **strtod;** su argumento *strSource* es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

La configuración de categoría **LC_NUMERIC** de la configuración regional actual determina el reconocimiento del carácter de punto de radio en *strSource*. Para obtener más información, vea [setlocale](setlocale-wsetlocale.md). Las funciones sin el sufijo **_l** utilizan la configuración regional actual; **_strtod_l** es idéntica a **_strtod_l** excepto que usan la *configuración regional* pasada en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no es **NULL**, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontró ningún dígito válido o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación señalada por *endptr*.

**strtod** espera que *strSource* apunte a una cadena de una de las siguientes formas:

[*espacio en blanco*] [*signo*] •*dígitos* [ *dígitos**de radio* ] &#124; *dígitos* *de radios* ? [e**e** &#124;*sign* **E**á [*sequence* *dígitos*de*signo*] [*espacio en blanco*] [*signo*] -**0x** &#124; **0X**á*hexdígitos* [ radix *hexdigits* **NAN** ] &#124;*radix* *radix* *hexdigits*- [a**p** &#124; **P**- [*signo*] *hexdígitos*] [*espacio en blanco*] [*signo*]**] INF** &#124; **INFINITY**- [*whitespace*]

El *espacio en blanco* inicial opcional puede constar de caracteres de espacio y tabulación, que se omiten; *signo* es más (+) o menos (-); *dígitos* son uno o más dígitos decimales; *los hexdígitos* son uno o más dígitos hexadecimales; *radix* es el carácter de punto de radio, ya sea un punto (.) en la configuración regional "C" predeterminada, o el valor específico de la configuración regional si la configuración regional actual es diferente o cuando se especifica la *configuración regional;* una *secuencia* es una secuencia de caracteres alfanuméricos o de subrayado. En las formas de números decimales y hexadecimales, si no aparecen dígitos antes del carácter de punto de radio, al menos uno debe aparecer después del carácter de punto de radio. En forma decimal, los dígitos decimales pueden ir seguidos de un exponente, que consta de una letra introductoria (**e** o **E**) y un entero con signo opcional. En la forma hexadecimal, los dígitos hexadecimales pueden ir seguidos de un exponente, que consta de una letra introductoria (**p** o **P**) y un entero hexadecimal con signo opcional que representa el exponente como una potencia de 2. En cualquier forma, si no aparece una parte de exponente ni un carácter de punto de radio, se supone que un carácter de punto de radio sigue el último dígito de la cadena. El caso se ignora en las formas **INF** y **NAN.** El primer carácter que no se ajusta a una de estas formas detiene el análisis.

Las versiones UCRT de estas funciones no admiten la conversión de letras exponentes de estilo Fortran (**d** o **D).** Esta extensión no estándar era compatible con versiones anteriores de CRT y puede que sea un cambio decisivo para el código. Las versiones De UCRT admiten cadenas hexadecimales y ida y vuelta de valores INF y NAN, que no se admitían en versiones anteriores. Esto también puede provocar cambios importantes en el código. Por ejemplo, la cadena "0x1a" se interpretaría por **strtod** como 0.0 en versiones anteriores, pero como 26.0 en la versión UCRT.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> o &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C: &lt;stdlib.h> o &lt;wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> o &lt;wchar.h> |

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strtod.c
// This program uses strtod to convert a
// string to a double-precision value; strtol to
// convert a string to long integer values; and strtoul
// to convert a string to unsigned long-integer values.
//

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   char   *string, *stopstring;
   double x;
   long   l;
   int    base;
   unsigned long ul;

   string = "3.1415926This stopped it";
   x = strtod( string, &stopstring );
   printf( "string = %s\n", string );
   printf("   strtod = %f\n", x );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "-10110134932This stopped it";
   l = strtol( string, &stopstring, 10 );
   printf( "string = %s\n", string );
   printf("   strtol = %ld\n", l );
   printf("   Stopped scan at: %s\n\n", stopstring );

   string = "10110134932";
   printf( "string = %s\n", string );

   // Convert string using base 2, 4, and 8:
   for( base = 2; base <= 8; base *= 2 )
   {
      // Convert the string:
      ul = strtoul( string, &stopstring, base );
      printf( "   strtol = %ld (base %d)\n", ul, base );
      printf( "   Stopped scan at: %s\n", stopstring );
   }
}
```

```Output
string = 3.1415926This stopped it
   strtod = 3.141593
   Stopped scan at: This stopped it

string = -10110134932This stopped it
   strtol = -2147483648
   Stopped scan at: This stopped it

string = 10110134932
   strtol = 45 (base 2)
   Stopped scan at: 34932
   strtol = 4423 (base 4)
   Stopped scan at: 4932
   strtol = 2134108 (base 8)
   Stopped scan at: 932
```

## <a name="see-also"></a>Consulte también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)<br/>
[strtol, wcstol, _strtol_l, _wcstol_l](strtol-wcstol-strtol-l-wcstol-l.md)<br/>
[strtoul, _strtoul_l, wcstoul, _wcstoul_l](strtoul-strtoul-l-wcstoul-wcstoul-l.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](atof-atof-l-wtof-wtof-l.md)<br/>
[localeconv](localeconv.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[_free_locale](free-locale.md)<br/>
