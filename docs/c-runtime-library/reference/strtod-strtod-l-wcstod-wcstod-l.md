---
title: strtod, _strtod_l, wcstod, _wcstod_l
ms.date: 10/20/2017
apiname:
- wcstod
- _wcstod_l
- _strtod_l
- strtod
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
ms.openlocfilehash: c8c2b3b491e2e7265829fa88580529dc757ace8c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62376476"
---
# <a name="strtod-strtodl-wcstod-wcstodl"></a>strtod, _strtod_l, wcstod, _wcstod_l

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

**strtod** devuelve el valor del número de punto flotante, excepto cuando la representación produciría desbordamiento, en cuyo caso la función devuelve +/-**HUGE_VAL**. El inicio de sesión de **HUGE_VAL** coincide con el signo del valor que no se puede representar. **strtod** devuelve 0 si se puede realizar ninguna conversión o se produce un subdesbordamiento.

**wcstod** devuelve valores de manera parecida a **strtod**. Para ambas funciones, **errno** está establecido en **ERANGE** si se produce desbordamiento o subdesbordamiento y se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Vea [_doserrno, errno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.

## <a name="remarks"></a>Comentarios

Cada función convierte la cadena de entrada *strSource* a un **doble**. El **strtod** función convierte *strSource* en un valor de precisión doble. **strtod** deja de leer la cadena *strSource* en el primer carácter que no se reconoce como parte de un número. Este puede ser el carácter nulo de terminación. **wcstod** es una versión con caracteres anchos de **strtod**; su *strSource* argumento es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstod**|**strtod**|**strtod**|**wcstod**|
|**_tcstod_l**|**_strtod_l**|**_strtod_l**|**_wcstod_l**|

El **LC_NUMERIC** valor de la categoría de la configuración regional actual determina el reconocimiento del carácter de punto base *strSource*. Para obtener más información, vea [setlocale](setlocale-wsetlocale.md). Las funciones sin el **_l** sufijo usar la configuración regional actual. **_strtod_l** es idéntico al **_strtod_l** salvo que usan el *configuración regional* pasado en su lugar. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Si *endptr* no **NULL**, un puntero al carácter que detuvo el análisis se almacena en la ubicación señalada por *endptr*. Si no se puede realizar ninguna conversión (no se encontró ningún dígito válido o se especificó una base no válida), el valor de *strSource* se almacena en la ubicación señalada por *endptr*.

**strtod** espera *strSource* para que apunte a una cadena de uno de los formatos siguientes:

[*espacio en blanco*] [*sesión*] {*dígitos* [*base* *dígitos*] &#124;  *radix* *dígitos*} [{**e** &#124; **E**} [*sesión*] *dígitos*] [*espacio en blanco*] [*sesión*] {**0 x** &#124; **0 X**} {*dígitos hexadecimales* [ *base* *dígitos hexadecimales*] &#124; *base* *dígitos hexadecimales*} [{**p** &#124; **P**} [*sesión*] *dígitos hexadecimales*] [*espacio en blanco*] [*sesión*] {} **INF** &#124; **infinito**} [*espacio en blanco*] [*sesión*]  **NAN** [*secuencia*]

El interlineado opcional *espacio en blanco* puede constar de caracteres de espacio y tabulación, que se omiten; *sesión* sea más (+) o menos (-); *dígitos* son uno o más dígitos decimales; *dígitos hexadecimales* son uno o más dígitos hexadecimales; *base* es el carácter de punto base, ya sea un punto (.) en la configuración regional "C" de forma predeterminada, o valor de la configuración regional específica si la configuración regional actual es diferente, o cuando *configuración regional* se especifica; un *secuencia* es una secuencia de alfanuméricos o caracteres de subrayado. En los formularios de número decimal y hexadecimales, si no aparece ningún dígito antes del carácter de punto base, al menos uno debe aparecer después del carácter de punto base. En el formato decimal, los dígitos decimales pueden ir seguidos por un exponente, que consta de una letra inicial (**e** o **E**) y un entero con signo optativo. En el formato hexadecimal, los dígitos hexadecimales pueden ir seguidos por un exponente, que consta de una letra inicial (**p** o **P**) y un entero hexadecimal con signo opcional que representa el exponente como una potencia de 2. En ambos casos, si aparece una parte exponencial ni un carácter de punto base, un carácter de punto base se supone que sigue al último dígito en la cadena. Mayúsculas y minúsculas se ignoran en ambos el **INF** y **NAN** formularios. El primer carácter que no se ajusta a uno de estos formularios detiene el análisis.

Las versiones UCRT de estas funciones no admiten la conversión de estilo Fortran (**d.** o **d.**) letras como exponente. Esta extensión no estándar era compatible con versiones anteriores de CRT y puede que sea un cambio decisivo para el código. Las versiones UCRT admiten cadenas hexadecimales e ida y vuelta de los valores de INF y NAN, que no se admitían en versiones anteriores. Esto puede hacer que los cambios importantes en el código. Por ejemplo, la cadena "0x1a" interpretaría **strtod** como 0,0 en versiones anteriores, pero como 26.0 en la versión UCRT.

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
