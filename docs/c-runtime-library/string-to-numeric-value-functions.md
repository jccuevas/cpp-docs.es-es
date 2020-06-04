---
title: Funciones de conversión de valores de cadena en valores numéricos
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tcstoui64
- _tcstoi64
helpviewer_keywords:
- parsing, numeric strings
- string conversion, to numeric values
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
ms.openlocfilehash: b9d8218bd5a3151e17b7ac380bb86c85dac3e6a3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944721"
---
# <a name="string-to-numeric-value-functions"></a>Funciones de conversión de valores de cadena en valores numéricos

- [strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)

- [strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)

- [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)

- [_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)

- [_strtoui64, _wcstoui64, _strtoui64_l, _wcstoui64_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)

## <a name="remarks"></a>Comentarios

Cada función de la familia **strtod** convierte una cadena terminada en NULL en un valor numérico. Las funciones disponibles se enumeran en la tabla siguiente.

|Función|DESCRIPCIÓN|
|--------------|-----------------|
|`strtod`|Convertir una cadena en un valor de punto flotante de precisión doble|
|`strtol`|Convertir una cadena en un entero largo|
|`strtoul`|Convertir una cadena en un entero largo sin signo|
|`_strtoi64`|Convertir una cadena en un entero `__int64` de 64 bits|
|`_strtoui64`|Convertir una cadena en un entero `__int64` sin signo de 64 bits|

`wcstod`, `wcstol`, `wcstoul` y `_wcstoi64` son versiones con caracteres anchos de `strtod`, `strtol`, `strtoul` y `_strtoi64`, respectivamente. El argumento de cadena para cada una de estas funciones de caracteres anchos es una cadena de caracteres anchos; en caso contrario, cada función se comporta de manera idéntica a su equivalente de caracteres de un solo byte.

La función `strtod` toma dos argumentos: el primero es la cadena de entrada y el segundo un puntero al carácter que finaliza el proceso de conversión. `strtol`, `strtoul`, **_strtoi64** y **_strtoui64** toman un tercer argumento como la base numérica que se va a usar en el proceso de conversión.

La cadena de entrada es una secuencia de caracteres que se puede interpretar como un valor numérico del tipo especificado. Cada función deja de leer la cadena en el primer carácter que no reconoce como parte de un número. Este puede ser el carácter nulo de terminación. Para `strtol`, `strtoul`, `_strtoi64` y `_strtoui64`, este carácter de terminación también puede ser el primer carácter numérico superior o igual que la base numérica proporcionada por el usuario.

Si el puntero proporcionado por el usuario a un carácter de final de conversión no se establece en **NULL** en el momento de la llamada, se almacenará un puntero al carácter que ha detenido el análisis en su lugar. Si no se puede realizar ninguna conversión (no se encontraron dígitos válidos o se ha especificado una base no válida), el valor del puntero de cadena se almacena en esa dirección.

`strtod` espera una cadena con el formato siguiente:

[*whitespace*] [*sign*] [`digits`] [ **.** `digits`] [ {**d** &#124; **D** &#124; **e** &#124; **E**}[*sign*]`digits`]

Un *whitespace* puede constar de caracteres de espacio o de tabulación, que se omiten; *sign* es más ( **+** ) o menos ( **-** ); y `digits` se refiere a uno o varios dígitos decimales. Si no aparece ningún dígito antes del carácter de base, debe aparecer al menos uno después del carácter de base. Los dígitos decimales pueden ir seguidos de un exponente, que consta de una letra inicial (**d**, **D**, **e** o **E**) y un entero con signo optativo. Si no aparece ni una parte exponencial ni un carácter de base, se supone que un carácter de base sigue al último dígito de la cadena. El primer carácter que no se ajusta a este formato detiene el análisis.

Las funciones `strtol`, `strtoul`, `_strtoi64` y `_strtoui64` esperan una cadena con el formato siguiente:

[*whitespace*] [{ **+** &#124; **-** }] [**0** [{ **x** &#124; **X** }]] [`digits`]

Si el argumento base está entre 2 y 36, se usa como base del número. Si es 0, los caracteres iniciales a los que se hace referencia mediante el puntero de la conversión final se usan para determinar la base. Si el primer carácter es 0 y el segundo carácter no es "x" ni "X", la cadena se interpreta como un entero octal; de otro modo, se interpreta como un número decimal. Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal. Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal. A las letras de la "a" a la "z" (o de la "A" a la "Z") se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que *base*. `strtoul` y `_strtoui64` permiten un prefijo de signo más ( **+** ) o menos ( **-** ); un signo menos inicial indica que el valor devuelto es negativo.

El valor de salida se ve afectado por el valor de la categoría `LC_NUMERIC` de la configuración regional; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el sufijo **_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa.

Cuando el valor devuelto por estas funciones provocaría un desbordamiento o subdesbordamiento, o cuando la conversión no es posible, se devuelven valores Case como se muestra a continuación:

|Función|Condición|Valor devuelto|
|--------------|---------------|--------------------|
|`strtod`|Desbordamiento|+/- `HUGE_VAL`|
|`strtod`|Subdesbordamiento o sin conversión|0|
|`strtol`|+ Desbordamiento|**LONG_MAX**|
|`strtol`|- Desbordamiento|**LONG_MIN**|
|`strtol`|Subdesbordamiento o sin conversión|0|
|`_strtoi64`|+ Desbordamiento|**_I64_MAX**|
|`_strtoi64`|- Desbordamiento|**_I64_MIN**|
|`_strtoi64`|Sin conversión|0|
|`_strtoui64`|Desbordamiento|**_UI64_MAX**|
|`_strtoui64`|Sin conversión|0|

**_I64_MAX**, _**I64_MIN** y **_UI64_MAX** se definen en LIMITS.H.

`wcstod`, `wcstol`, `wcstoul`, `_wcstoi64` y `_wcstoui64` son versiones de caracteres anchos de `strtod`, `strtol`, `strtoul`, `_strtoi64` y `_strtoui64`, respectivamente; el puntero a un argumento del final de conversión para cada una de estas funciones de caracteres anchos es una cadena de caracteres anchos. En caso contrario, cada una de estas funciones de caracteres anchos se comporta de manera idéntica a su equivalente de caracteres de un solo byte.

## <a name="see-also"></a>Vea también

[Conversión de datos](../c-runtime-library/data-conversion.md)<br/>
[Configuración regional](../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[Compatibilidad con el punto flotante](../c-runtime-library/floating-point-support.md)<br/>
[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)
