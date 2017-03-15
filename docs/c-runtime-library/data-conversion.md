---
title: "Conversión de datos | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.conversions
dev_langs:
- C++
helpviewer_keywords:
- data conversion routines [C++]
- converting data
ms.assetid: b15b5268-7467-49f1-bf95-5299b598f94c
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 08bf22d6f41dbd528e229a117f4ebc6a9e8aff0c
ms.lasthandoff: 02/24/2017

---
# <a name="data-conversion"></a>Conversión de datos
Estas rutinas cambian el formato de los datos a otro distinto. Estas rutinas se suelen ejecutar más rápidamente que las que usted pueda escribir. Cada rutina que comienza con un prefijo `to` se implementa como función y como macro. Vea [Elegir entre funciones y macros](../c-runtime-library/recommendations-for-choosing-between-functions-and-macros.md) para obtener información sobre cómo elegir una implementación.  
  
### <a name="data-conversion-routines"></a>Rutinas de conversión de datos  
  
|Rutina|Uso|Equivalente de .NET Framework|  
|-------------|---------|-------------------------------|  
|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Busca el valor absoluto de un entero|[System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convierte la cadena a `float`|[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convierte la cadena a `int`|[System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx), [System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convierte la cadena a `__int64`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx), [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convierte la cadena a `long`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx), [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)|  
|[_ecvt](../c-runtime-library/reference/ecvt.md), [_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|Convierte `double` en una cadena de la longitud especificada|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_fcvt](../c-runtime-library/reference/fcvt.md), [_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|Convierte `double` en una cadena con el número especificado de dígitos después del separador decimal|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_gcvt](../c-runtime-library/reference/gcvt.md), [_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|Convierte el número `double` en una cadena y la almacena en el búfer|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_itoa, _i64toa, _ui64toa, _itow, _i64tow, _ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md), [_itoa_s, _i64toa_s, _ui64toa_s, _itow_s, _i64tow_s, _ui64tow_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|Convierte `int` o `__int64` en una cadena|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Busca el valor absoluto de un entero `long`|[System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[llabs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|Busca el valor absoluto de un entero `long long`|[System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)|  
|[_ltoa, _ltow](../c-runtime-library/reference/ltoa-ltow.md), [_ltoa_s, _ltow_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|Convierte `long` en una cadena|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[_mbbtombc, _mbbtombc_l](../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)|Convierte el carácter multibyte de un byte en el carácter multibyte de 2 bytes correspondiente|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Convierte el carácter de JIS en carácter de Japan Microsoft (JMS)|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_mbcjistojms, _mbcjistojms_l, _mbcjmstojis, _mbcjmstojis_l](../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)|Convert el carácter de JMS en carácter de JIS|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Convierte el carácter multibyte en código hiragana de un byte|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l](../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)|Convierta el carácter multibyte en código katakana de un byte|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_mbctombb, _mbctombb_l](../c-runtime-library/reference/mbctombb-mbctombb-l.md)|Convierte el carácter multibyte de dos bytes en el carácter multibyte de 1 byte correspondiente|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convierte la secuencia de caracteres multibyte en la secuencia correspondiente de caracteres anchos|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convierte el carácter multibyte en el carácter ancho correspondiente|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Convierte la cadena a `double`|[System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Convierte una cadena en entero `long`|[System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)|  
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Convierte una cadena en entero `unsigned long`|[System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)|  
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Cambia la cadena a un formato intercalado en función de información específica de la configuración regional|[System::IFormattable::ToString](https://msdn.microsoft.com/en-us/library/system.iformattable.tostring.aspx)|  
|[toascii, __toascii](../c-runtime-library/reference/toascii-toascii.md)|Convierte un carácter en código ASCII||  
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Prueba el carácter y lo cambia a minúscula si está en mayúscula|[System::Char::ToLower](https://msdn.microsoft.com/en-us/library/system.char.tolower.aspx)|  
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)|Cambia el carácter a minúscula en todos los casos|[System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)|  
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Prueba el carácter y lo cambia a mayúscula si está en minúscula|[System::Char::ToUpper](https://msdn.microsoft.com/en-us/library/system.char.toupper.aspx)|  
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|Cambia el carácter a mayúscula en todos los casos|[System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)|  
|[_ultoa, _ultow](../c-runtime-library/reference/ultoa-ultow.md), [_ultoa_s, _ultow_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|Convierte `unsigned``long` en una cadena|[System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)|  
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convierte la secuencia de caracteres anchos en la secuencia correspondiente de caracteres multibyte|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convierte el carácter ancho en el carácter multibyte correspondiente|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convierte una cadena de caracteres anchos en `double`|[System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx), [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx), [System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx), [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)|  
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convierte una cadena de caracteres anchos en `int`|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convierte una cadena de caracteres anchos en `__int64`|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convierte una cadena de caracteres anchos en `long`|No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).|  
  
## <a name="see-also"></a>Vea también  
 [Rutinas en tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)
