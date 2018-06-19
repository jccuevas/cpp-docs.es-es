---
title: Conversión de datos | Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a0260ebe37e0656f2078b247017d9f02ccc88474
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392450"
---
# <a name="data-conversion"></a>Conversión de datos

Estas rutinas cambian el formato de los datos a otro distinto. Estas rutinas se suelen ejecutar más rápidamente que las que usted pueda escribir. Cada rutina que comienza con un prefijo *to* se implementa como función y como macro. Vea [Choosing Between Functions and Macros](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) (Elegir entre funciones y macros) para obtener información sobre cómo elegir una implementación.

## <a name="data-conversion-routines"></a>Rutinas de conversión de datos

|Rutina|Usar|
|-------------|---------|
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Busca el valor absoluto de un entero|
|[atof, _atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convierte la cadena a **float**|
|[atoi, _atoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convierte una cadena en **int**|
|[_atoi64, _atoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convierte una cadena en **__int64** o **long long**|
|[atol, _atol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convierte una cadena en **long**|
|[c16rtomb, c32rtomb](../c-runtime-library/reference/c16rtomb-c32rtomb1.md)|Convierte el carácter UTF-16 o UTF-32 en un carácter multibyte equivalente|
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Convierte **double** en una cadena de la longitud especificada|
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Convierte **double** en una cadena con el número especificado de dígitos después del separador decimal|
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Convierte el número **double** en una cadena y la almacena en el búfer|
|[_itoa, _ltoa, _ultoa, _i64toa, _ui64toa, _itow, _ltow, ultow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-itow.md), [_itoa_s, _ltoa_s, _ultoa_s, _i64toa_s, _ui64toa_s, _itow_s, _ltow_s, _ultow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-itow-s.md)|Convierte tipos de enteros en cadenas|
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Encuentra el valor absoluto de un entero **long**|
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Encuentra el valor absoluto de un entero **long long**|
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Convierte el carácter multibyte de un byte en el carácter multibyte de 2 bytes correspondiente|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Convierte el carácter de JIS en carácter de Japan Microsoft (JMS)|
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Convert el carácter de JMS en carácter de JIS|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Convierte el carácter multibyte en código hiragana de un byte|
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Convierta el carácter multibyte en código katakana de un byte|
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Convierte el carácter multibyte de dos bytes en el carácter multibyte de 1 byte correspondiente|
|[mbrtoc16, mbrtoc32](../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)|Convierte el carácter multibyte en un carácter UTF-16 o UTF-32 equivalente|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convierte la secuencia de caracteres multibyte en la secuencia correspondiente de caracteres anchos|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convierte el carácter multibyte en el carácter ancho correspondiente|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Convierte una cadena a **double**|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Convierte una cadena en un entero **long**|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Convertir una cadena en un entero **unsigned long**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Cambia la cadena a un formato intercalado en función de información específica de la configuración regional|
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Convierte un carácter en código ASCII||
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Prueba el carácter y lo cambia a minúscula si está en mayúscula|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Cambia el carácter a minúscula en todos los casos|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Prueba el carácter y lo cambia a mayúscula si está en minúscula|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Cambia el carácter a mayúscula en todos los casos|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convierte la secuencia de caracteres anchos en la secuencia correspondiente de caracteres multibyte|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convierte el carácter ancho en el carácter multibyte correspondiente|
|[_wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convierte una cadena de caracteres anchos en **double**|
|[_wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convierte una cadena de caracteres anchos en **int**|
|[_wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convierte una cadena de caracteres anchos en **__int64** o **long long**|
|[_wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convierte una cadena de caracteres anchos en **long**|

## <a name="see-also"></a>Vea también

[Rutinas en tiempo de ejecución Universal C por categoría](../c-runtime-library/run-time-routines-by-category.md)<br/>
