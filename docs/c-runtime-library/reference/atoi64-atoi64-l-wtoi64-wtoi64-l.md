---
title: _atoi64, _atoi64_l, _wtoi64, _wtoi64_l
ms.date: 4/2/2020
api_name:
- _atoi64_l
- _wtoi64
- _atoi64
- _wtoi64_l
- _o__atoi64
- _o__atoi64_l
- _o__wtoi64
- _o__wtoi64_l
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
- _atoi64
- _tstoi64
- _ttoi64
- wtoi64
- _tstoi64_l
- atoi64
- _wtoi64_l
- _wtoi64
- wtoi64_l
- _atoi64_l
- atoi64_l
helpviewer_keywords:
- tstoi64 function
- wtoi64 function
- atoi64_l function
- _ttoi64 function
- string conversion, to integers
- wtoi64_l function
- atoi64 function
- _tstoi64 function
- _atoi64_l function
- _wtoi64_l function
- ttoi64 function
- _wtoi64 function
- _atoi64 function
ms.assetid: 2c3e30fd-545d-4222-8364-0c5905df9526
ms.openlocfilehash: 555cd27e87324141f21bdd7ef12f9ff8ea1a4e09
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913569"
---
# <a name="_atoi64-_atoi64_l-_wtoi64-_wtoi64_l"></a>_atoi64, _atoi64_l, _wtoi64, _wtoi64_l

Convierte una cadena en un entero de 64 bits.

## <a name="syntax"></a>Sintaxis

```C
__int64 _atoi64(
   const char *str
);
__int64 _wtoi64(
   const wchar_t *str
);
__int64 _atoi64_l(
   const char *str,
   _locale_t locale
);
__int64 _wtoi64_l(
   const wchar_t *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*CAD*<br/>
Cadena que se va a convertir.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Cada función devuelve el valor de **__int64** generado al interpretar los caracteres de entrada como un número. El valor devuelto es 0 para **_atoi64** si la entrada no se puede convertir en un valor de ese tipo.

En caso de desbordamiento con valores enteros positivos grandes, **_atoi64** devuelve **I64_MAX** y **I64_MIN** en caso de desbordamiento con valores enteros negativos grandes.

En todos los casos fuera del intervalo, **errno** se establece en **ERANGE**. Si el parámetro pasado es **null**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven 0.

## <a name="remarks"></a>Observaciones

Estas funciones convierten una cadena de caracteres en un valor entero de 64 bits.

La cadena de entrada es una secuencia de caracteres que se puede interpretar como un valor numérico del tipo especificado. La función deja de leer la cadena de entrada en el primer carácter que no reconoce como parte de un número. Es posible que este carácter sea el carácter nulo ("\0" o L"\0") que termina la cadena.

El argumento *Str* para **_atoi64** tiene el formato siguiente:

> [*espacio en blanco*] [*signo*] [*dígitos*]

Un espacio en *blanco* consta de caracteres de espacio o tabulación, que se omiten; el *signo* es más (+) o menos (-); y los *dígitos* son uno o más dígitos.

**_wtoi64** es idéntica a **_atoi64** , salvo que toma una cadena de caracteres anchos como parámetro.

Las versiones de estas funciones con el sufijo **_L** son idénticas, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tstoi64**|**_atoi64**|**_atoi64**|**_wtoi64**|
|**_ttoi64**|**_atoi64**|**_atoi64**|**_wtoi64**|

## <a name="requirements"></a>Requisitos

|Rutinas|Encabezado necesario|
|--------------|---------------------|
|**_atoi64**, **_atoi64_l**|\<stdlib.h>|
|**_wtoi64**, **_wtoi64_l**|\<stdlib.h> o \<wchar.h>|

## <a name="example"></a>Ejemplo

Este programa muestra cómo se pueden convertir los números almacenados como cadenas en valores numéricos mediante las funciones de **_atoi64** .

```C
// crt_atoi64.c
// This program shows how numbers stored as
// strings can be converted to numeric values
// using the _atoi64 functions.
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>

int main( void )
{
    char    *str = NULL;
    __int64 value = 0;

    // An example of the _atoi64 function
    // with leading and trailing white spaces.
    str = "  -2309 ";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an arbitrary decimal point.
    str = "314127.64";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );

    // Another example of the _atoi64 function
    // with an overflow condition occurring.
    str = "3336402735171707160320";
    value = _atoi64( str );
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );
    if (errno == ERANGE)
    {
       printf("Overflow condition occurred.\n");
    }
}
```

```Output
Function: _atoi64( "  -2309 " ) = -2309
Function: _atoi64( "314127.64" ) = 314127
Function: _atoi64( "3336402735171707160320" ) = -1
Overflow condition occurred.
```

## <a name="see-also"></a>Consulta también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[_ecvt](ecvt.md)<br/>
[_fcvt](fcvt.md)<br/>
[_gcvt](gcvt.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)<br/>
