---
title: atof, _atof_l, _wtof, _wtof_l
ms.date: 04/05/2018
api_name:
- _wtof_l
- atof
- _atof_l
- _wtof
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
- _tstof
- _ttof
- atof
- stdlib/atof
- math/atof
- _atof_l
- stdlib/_atof_l
- math/_atof_l
- _wtof
- corecrt_wstdlib/_wtof
- _wtof_l
- corecrt_wstdlib/_wtof_l
helpviewer_keywords:
- tstof function
- atof_l function
- _atof_l function
- atof function
- _tstof function
- _ttof function
- wtof function
- _wtof_l function
- ttof function
- wtof_l function
- _wtof function
- string conversion, to floating point values
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
ms.openlocfilehash: a624ae9f900395ed2117ed2bb89e2768c64daba9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939571"
---
# <a name="atof-_atof_l-_wtof-_wtof_l"></a>atof, _atof_l, _wtof, _wtof_l

Convertir una cadena a un valor double.

## <a name="syntax"></a>Sintaxis

```C
double atof(
   const char *str
);
double _atof_l(
   const char *str,
   _locale_t locale
);
double _wtof(
   const wchar_t *str
);
double _wtof_l(
   const wchar_t *str,
   _locale_t locale
);
```

## <a name="parameters"></a>Parámetros

*str*<br/>
Cadena que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada función devuelve el valor **Double** generado al interpretar los caracteres de entrada como un número. El valor devuelto es 0.0 si la entrada no se puede convertir en un valor de ese tipo.

En todos los casos fuera del intervalo, **errno** se establece en **ERANGE**. Si el parámetro pasado es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven 0.

## <a name="remarks"></a>Comentarios

Estas funciones convierten una cadena de caracteres en un valor de punto flotante de doble precisión.

La cadena de entrada es una secuencia de caracteres que se puede interpretar como un valor numérico del tipo especificado. La función deja de leer la cadena de entrada en el primer carácter que no reconoce como parte de un número. Es posible que este carácter sea el carácter nulo ("\0" o L"\0") que termina la cadena.

El argumento *Str* para **atof** y **_wtof** tiene el formato siguiente:

[*espacio en blanco*] [*signo*] [*dígitos*] [ __.__ *dígitos*] [{**e** &#124; **e** } [*signo*]*dígitos*]

Un espacio en *blanco* consta de caracteres de espacio o tabulación, que se omiten; el *signo* es más (+) o menos (-); y los *dígitos* son uno o más dígitos decimales. Si no aparece ningún dígito antes del separador decimal, debe aparecer al menos uno después. Los dígitos decimales pueden ir seguidos de un exponente, que consta de una letra de presentación (**e**, o **e**) y un entero decimal con signo opcional.

Las versiones de UCRT de estas funciones no admiten la conversión de Letras de exponente de estilo Fortran (**d** o **d**). Esta extensión no estándar era compatible con versiones anteriores de CRT y puede que sea un cambio decisivo para el código.

Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que utilizan el parámetro de *configuración regional* que se pasa en lugar de la configuración regional actual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstof**|**atof**|**atof**|**_wtof**|
|**_ttof**|**atof**|**atof**|**_wtof**|

## <a name="requirements"></a>Requisitos

|Rutinas|Encabezado necesario|
|------------------|---------------------|
|**atof**, **_atof_l**|C: \<math.h> o \<stdlib.h> C++: \<cstdlib>, \<stdlib.h>, \<cmath> o \<math.h>|
|**_wtof**, **_wtof_l**|C: \<stdlib.h> o \<wchar.h> C++: \<cstdlib>, \<stdlib.h> o \<wchar.h>|

## <a name="example"></a>Ejemplo

Este programa muestra cómo se pueden convertir los números almacenados como cadenas en valores numéricos mediante las funciones **atof** y **_atof_l** .

```C
// crt_atof.c
//
// This program shows how numbers stored as
// strings can be converted to numeric
// values using the atof and _atof_l functions.

#include <stdlib.h>
#include <stdio.h>
#include <locale.h>

int main(void)
{
    char    *str = NULL;
    double value = 0;
    _locale_t fr = _create_locale(LC_NUMERIC, "fr-FR");

    // An example of the atof function
    // using leading and training spaces.
    str = "  3336402735171707160320 ";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // Another example of the atof function
    // using the 'E' exponential formatting keyword.
    str = "3.1412764583E210";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);

    // An example of the atof and _atof_l functions
    // using the 'e' exponential formatting keyword
    // and showing different decimal point interpretations.
    str = "  -2,309e-25";
    value = atof(str);
    printf("Function: atof(\"%s\") = %e\n", str, value);
    value = _atof_l(str, fr);
    printf("Function: _atof_l(\"%s\", fr)) = %e\n", str, value);
}
```

```Output
Function: atof("  3336402735171707160320 ") = 3.336403e+21
Function: atof("3.1412764583E210") = 3.141276e+210
Function: atof("  -2,309e-25") = -2.000000e+00
Function: _atof_l("  -2,309e-25", fr)) = -2.309000e-25
```

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
