---
title: localeconv | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: localeconv
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
apitype: DLLExport
f1_keywords: localeconv
dev_langs: C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: aa001a4c8dde1337eb576ae3a2c78108e4cb3199
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="localeconv"></a>localeconv
Obtiene información detallada sobre la configuración regional.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct lconv *localeconv( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 `localeconv` devuelve un puntero a un objeto rellenado de tipo [struct lconv](../../c-runtime-library/standard-types.md). Los valores contenidos en el objeto se copian de la configuración regional en almacenamiento local de subprocesos y se puede sobrescribir con las llamadas subsiguientes a `localeconv`. Los cambios realizados en los valores de este objeto no modifican la configuración regional. Las llamadas a [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) con los valores `category` `LC_ALL`, `LC_MONETARY` o `LC_NUMERIC` sobrescriben el contenido de la estructura.  
  
## <a name="remarks"></a>Comentarios  
 La función `localeconv` obtiene información detallada sobre el formato numérico de la configuración regional actual. Esta información se almacena en una estructura de tipo `lconv`. El `lconv` estructura, definida en la configuración regional. H, contiene los miembros siguientes:  
  
 `char *decimal_point, wchar_t *_W_decimal_point`  
 Carácter de separador decimal para las cantidades no monetarias.  
  
 `char *thousands_sep, wchar_t *_W_thousands_sep`  
 Carácter que separa grupos de dígitos a la izquierda del separador decimal para las cantidades no monetarias.  
  
 `char *grouping`  
 Puntero a un `char`-tamaño entero que contiene el tamaño de cada grupo de dígitos en cantidades monetarias.  
  
 `char *int_curr_symbol, wchar_t *_W_int_curr_symbol`  
 Símbolo de moneda internacional para la configuración regional actual. Los tres primeros caracteres especifican el símbolo de moneda internacional alfabético como se define en el estándar *Códigos ISO 4217 para la representación de las monedas y tipos de fondos*. El cuarto carácter (inmediatamente antes del carácter nulo) separa el símbolo de moneda internacional de la cantidad de moneda.  
  
 `char *currency_symbol, wchar_t *_W_currency_symbol`  
 Símbolo de moneda local de la configuración regional actual.  
  
 `char *mon_decimal_point, wchar_t *_W_mon_decimal_point`  
 Carácter de separador decimal para las cantidades monetarias.  
  
 `char *mon_thousands_sep, wchar_t *_W_mon_thousands_sep`  
 Separador de grupos de dígitos a la izquierda de la posición decimal en las cantidades monetarias.  
  
 `char *mon_grouping`  
 Puntero a un `char`-tamaño entero que contiene el tamaño de cada grupo de dígitos en cantidades monetarias.  
  
 `char *positive_sign, wchar_t *_W_positive_sign`  
 Cadena que denota el signo de las cantidades de moneda no negativas.  
  
 `char *negative_sign, wchar_t *_W_negative_sign`  
 Cadena que denota el signo de las cantidades de moneda negativas.  
  
 `char int_frac_digits`  
 Número de dígitos a la derecha del separador decimal en las cantidades de moneda con formato internacional.  
  
 `char frac_digits`  
 Número de dígitos a la derecha del separador decimal en las cantidades de moneda con formato.  
  
 `char p_cs_precedes`  
 Se establece en 1 si el símbolo de moneda precede al valor de cantidad de moneda no negativo con formato. Se establece en 0 si el símbolo sigue al valor.  
  
 `char p_sep_by_space`  
 Se establece en 1 si el símbolo de moneda está separado por un espacio del valor de la cantidad de moneda no negativa con formato. Se establece en 0 si no hay ninguna separación de espacio.  
  
 `char n_cs_precedes`  
 Se establece en 1 si el símbolo de moneda precede al valor de cantidad de moneda negativo con formato. Se establece en 0 si el símbolo aparece a continuación del valor.  
  
 `char n_sep_by_space`  
 Se establece en 1 si el símbolo de moneda está separado por un espacio del valor de la cantidad de moneda negativa con formato. Se establece en 0 si no hay ninguna separación de espacio.  
  
 `char p_sign_posn`  
 Posición de signo positivo en cantidades de moneda no negativas con formato.  
  
 `char n_sign_posn`  
 Posición de signo positivo en cantidades de moneda negativas con formato.  
  
Excepto según lo especificados, miembros de la `lconv` estructura que tienen `char *` y `wchar_t *` versiones son punteros a cadenas. Cualquiera de ellos que sea igual a `""` (o `L""` para `wchar_t *`) tiene una longitud de cero o no se admite en la configuración regional actual. Tenga en cuenta que `decimal_point` y `_W_decimal_point` siempre son compatibles y tienen una longitud distinta de cero.  
  
Los miembros `char` de la estructura son números no negativos pequeños, no caracteres. Cualquiera de estos que es igual a `CHAR_MAX` no se admite en la configuración regional actual.  
  
Los valores de `grouping` y `mon_grouping` se interpretan según las reglas siguientes:  
  
- `CHAR_MAX`-No realice ninguna agrupación.  
  
- 0 - use el elemento anterior para cada uno de los dígitos restantes.  
  
- *n*-Número de dígitos que componen el grupo actual. Se examina el siguiente elemento para determinar el tamaño del siguiente grupo de dígitos antes del grupo actual.  
  
Los valores de `int_curr_symbol` se interpretan según las reglas siguientes:  
  
-   Los tres primeros caracteres especifican el símbolo de moneda internacional alfabético como se define en el estándar *Códigos ISO 4217 para la representación de las monedas y tipos de fondos*.  
  
-   El cuarto carácter (inmediatamente antes del carácter nulo) separa el símbolo de moneda internacional de la cantidad de moneda.  
  
Los valores de `p_cs_precedes` y `n_cs_precedes` se interpretan según las reglas siguientes (el `n_cs_precedes` regla está entre paréntesis):  
  
- 0 - símbolo de divisa sigue al valor para el valor de moneda con formato (negativo) no negativo.  
  
- 1 - símbolo de divisa precede al valor para el valor de moneda con formato (negativo) no negativo.  
  
Los valores de `p_sep_by_space` y `n_sep_by_space` se interpretan según las reglas siguientes (el `n_sep_by_space` regla está entre paréntesis):  
  
- 0 - símbolo de moneda se separa de valor por el espacio de valor de moneda con formato (negativo) no negativo.  
  
- 1 - no hay una separación de espacio entre el símbolo de moneda y el valor para el valor de moneda con formato (negativo) no negativo.  
  
Los valores de `p_sign_posn` y `n_sign_posn` se interpretan según las reglas siguientes:  
  
- 0 - paréntesis rodean símbolos de cantidad y moneda.  
  
- 1 - sign cadena precede a los símbolos de cantidad y moneda.  
  
- 2 - cadena de inicio de sesión sigue símbolos de cantidad y moneda.  
  
- 3 - inicio de sesión cadena precede inmediatamente a símbolo de divisa.  
  
- 4 - inicio de sesión inmediatamente cadena el símbolo de moneda se indica a continuación.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`localeconv`|\<locale.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [strcoll (Funciones)](../../c-runtime-library/strcoll-functions.md)   
 [strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)