---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 10/20/2017
api_name:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
ms.openlocfilehash: 5372525eb99dc9d39e31b10def0377c9aad5296c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946490"
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

**strtod** devuelve el valor del número de punto flotante, excepto cuando la representación provocaría un desbordamiento, en cuyo caso la función devuelve +/-**HUGE_VAL**. El signo de **HUGE_VAL** coincide con el signo del valor que no se puede representar. **strtod** devuelve 0 si no se puede realizar ninguna conversión o si se produce un subdesbordamiento.

**wcstod** devuelve valores de forma análoga a **strtod**. En ambas funciones, **errno** se establece en **ERANGE** si se produce desbordamiento o subdesbordamiento y se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

Cada función convierte la cadena de entrada *strSource* en un **valor Double**. La función **strtod** convierte *strSource* en un valor de precisión doble. **strtod** deja de leer la cadena *strSource* en el primer carácter que no reconoce como parte de un número. Este puede ser el carácter nulo de terminación. **wcstod** es una versión con caracteres anchos de **strtod**; su argumento *strSource* es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

El valor de la categoría **LC_NUMERIC** de la configuración regional actual determina el reconocimiento del carácter de punto de base en *strSource*. Para obtener más información, vea [setlocale](setlocale-wsetlocale.md). Las funciones sin el sufijo **_L** usan la configuración regional actual; **_strtod_l** es idéntico a **_strtod_l** , salvo que usa la *configuración regional* que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no es **null**, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que apunta *endptr*. Si no se puede realizar ninguna conversión (no se encontraron dígitos válidos o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación a la que apunta *endptr*.

**strtod** espera que *strSource* señale a una cadena de uno de los formatos siguientes:

[*espacio en blanco*] [*signo*] {*dígitos* [ *dígitos*de base &#124; ] *dígitos*de *base* } [{**e** &#124; **e**} [*signo*] *dígitos*] [*espacio en blanco*] [*signo*] {**0x** &#124; **0x**} {*hexdigits* [*base* *hexdigits*] &#124;  *base* *hexdigits*} [{**p** &#124; **p**} [*signo*] *hexdigits*] [*espacio en blanco*] [*signo*] {%**INF** &#124; **infinito**} [*espacio en blanco*] [ *signo*] **Nan** [*secuencia*]

El espacio en *blanco* inicial opcional puede constar de caracteres de espacio y tabulación, que se omiten; el *signo* es más (+) o menos (-); los *dígitos* son uno o más dígitos decimales; *hexdigits* son uno o más dígitos hexadecimales; la *base* es el carácter de punto de base, ya sea un punto (.) en la configuración regional "C" predeterminada o el valor específico de la configuración regional si la configuración regional actual es diferente o se especifica la *configuración regional* ; una *secuencia* es una secuencia de caracteres alfanuméricos o de subrayado. En los formatos de número decimal y hexadecimal, si no aparece ningún dígito antes del carácter de punto de base, debe aparecer al menos uno después del carácter de punto de base. En la forma decimal, los dígitos decimales pueden ir seguidos de un exponente, que consta de una letra de presentación (**e** o **e**) y un entero con signo opcional. En el formato hexadecimal, los dígitos hexadecimales pueden ir seguidos de un exponente, que consta de una letra de introducción (**p** o **p**) y un entero hexadecimal con signo opcional que representa el exponente como potencia de 2. En cualquier forma, si no aparece una parte del exponente ni un carácter de punto de base, se supone que un carácter de punto de base sigue el último dígito de la cadena. El caso se omite en los formatos **INF** y **Nan** . El primer carácter que no se ajusta a uno de estos formularios detiene el examen.

Las versiones de UCRT de estas funciones no admiten la conversión de Letras de exponente de estilo Fortran (**d** o **d**). Esta extensión no estándar era compatible con versiones anteriores de CRT y puede que sea un cambio decisivo para el código. Las versiones de UCRT admiten cadenas hexadecimales y recorridos de ida y vuelta de los valores INF y NAN, que no se admitían en versiones anteriores. Esto también puede producir cambios importantes en el código. Por ejemplo, **strtod** interpretaría la cadena "0x1A" como 0,0 en las versiones anteriores, pero como 26,0 en la versión de UCRT.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtod**, **_strtod_l**|C: &lt;stdlib.h> C++: &lt;cstdlib> o &lt;stdlib.h> |
|**wcstod**, **_wcstod_l**|C: &lt;stdlib.h> o &lt;wchar.h> C++: &lt;cstdlib>, &lt;stdlib.h> o &lt;wchar.h> |

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

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
