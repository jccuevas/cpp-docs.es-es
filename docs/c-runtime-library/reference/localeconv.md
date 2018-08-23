---
title: localeconv | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- localeconv
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- localeconv
dev_langs:
- C++
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7f4e8a20ef31f4379e7ddf6b7425fd7ecc70294a
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2018
ms.locfileid: "42572769"
---
# <a name="localeconv"></a>localeconv

Obtiene información detallada sobre la configuración regional.

## <a name="syntax"></a>Sintaxis

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Valor devuelto

**localeconv** devuelve un puntero a un objeto rellenado de tipo [struct lconv](../../c-runtime-library/standard-types.md). Los valores contenidos en el objeto se copian de la configuración regional en almacenamiento local de subprocesos y se puede sobrescribir con las llamadas subsiguientes a **localeconv**. Los cambios realizados en los valores de este objeto no modifican la configuración regional. Las llamadas a [setlocale](setlocale-wsetlocale.md) con *categoría* valores de **LC_ALL**, **LC_MONETARY**, o **LC_NUMERIC** sobrescribir el contenido de la estructura.

## <a name="remarks"></a>Comentarios

El **localeconv** función obtiene información detallada sobre el formato numérico para la configuración regional actual. Esta información se almacena en una estructura de tipo **lconv**. La estructura **lconv**, definida en LOCALE.H, contiene los miembros siguientes:

|Campo|Significado|
|-|-|
decimal_point,<br/>_W_decimal_point|Puntero al carácter para las cantidades no monetarias de separador decimal.
thousands_sep,<br/>_W_thousands_sep|Puntero al carácter que separa grupos de dígitos a la izquierda del separador decimal para las cantidades no monetarias.
agrupar|Puntero a un **char**-tamaño entero que contiene el tamaño de cada grupo de dígitos en cantidades no monetarias.
int_curr_symbol,<br/>_W_int_curr_symbol|Puntero al símbolo de moneda internacional para la configuración regional actual. Los tres primeros caracteres especifican el símbolo de moneda internacional alfabético como se define en el estándar *Códigos ISO 4217 para la representación de las monedas y tipos de fondos*. El cuarto carácter (inmediatamente antes del carácter nulo) separa el símbolo de moneda internacional de la cantidad de moneda.
currency_symbol,<br/>_W_currency_symbol|Puntero al símbolo de moneda local para la configuración regional actual.
mon_decimal_point,<br/>_W_mon_decimal_point|Puntero al carácter para las cantidades de moneda de separador decimal.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Puntero al separador de grupos de dígitos a la izquierda de la posición decimal en las cantidades monetarias.
mon_grouping|Puntero a un **char**-tamaño entero que contiene el tamaño de cada grupo de dígitos en cantidades monetarias.
positive_sign,<br/>_W_positive_sign|Cadena que denota el signo de las cantidades de moneda no negativas.
negative_sign,<br/>_W_negative_sign|Cadena que denota el signo de las cantidades de moneda negativas.
int_frac_digits|Número de dígitos a la derecha del separador decimal en las cantidades de moneda con formato internacional.
frac_digits|Número de dígitos a la derecha del separador decimal en las cantidades de moneda con formato.
p_cs_precedes|Se establece en 1 si el símbolo de moneda precede al valor de cantidad de moneda no negativo con formato. Se establece en 0 si el símbolo sigue al valor.
p_sep_by_space|Se establece en 1 si el símbolo de moneda está separado por un espacio del valor de la cantidad de moneda no negativa con formato. Se establece en 0 si no hay ninguna separación de espacio.
n_cs_precedes|Se establece en 1 si el símbolo de moneda precede al valor de cantidad de moneda negativo con formato. Se establece en 0 si el símbolo aparece a continuación del valor.
n_sep_by_space|Se establece en 1 si el símbolo de moneda está separado por un espacio del valor de la cantidad de moneda negativa con formato. Se establece en 0 si no hay ninguna separación de espacio.
p_sign_posn|Posición de signo positivo en cantidades de moneda no negativas con formato.
n_sign_posn|Posición de signo positivo en cantidades de moneda negativas con formato.

Excepto según lo especificados, miembros de la **lconv** estructura que tienen `char *` y `wchar_t *` versiones son punteros a cadenas. Cualquiera de estos que sea igual a **""** (o **L ""** para **wchar_t \*** ) es de longitud cero o no se admite en la configuración regional actual. Tenga en cuenta que **decimal_point** y **_W_decimal_point** siempre son compatibles y de longitud distinta de cero.

El **char** los miembros de la estructura son números no negativos pequeños, no de caracteres. Cualquiera de estos que sea igual a **CHAR_MAX** no se admite en la configuración regional actual.

Los valores de **agrupación** y **mon_grouping** se interpretan según las reglas siguientes:

- **CHAR_MAX** -no realice ninguna agrupación más.

- 0 - use el elemento anterior para cada uno de los dígitos restantes.

- *n* -número de dígitos que componen el grupo actual. Se examina el siguiente elemento para determinar el tamaño del siguiente grupo de dígitos antes del grupo actual.

Los valores de **int_curr_symbol** se interpretan según las reglas siguientes:

- Los tres primeros caracteres especifican el símbolo de moneda internacional alfabético como se define en el estándar *Códigos ISO 4217 para la representación de las monedas y tipos de fondos*.

- El cuarto carácter (inmediatamente antes del carácter nulo) separa el símbolo de moneda internacional de la cantidad de moneda.

Los valores de **p_cs_precedes** y **n_cs_precedes** se interpretan según las reglas siguientes (la regla **n_cs_precedes** aparece entre paréntesis):

- 0: símbolo de moneda sigue al valor no negativo (negativo) con formato valor de moneda.

- -1 símbolo de moneda de precede al valor no negativo (negativo) con formato valor de moneda.

Los valores de **p_sep_by_space** y **n_sep_by_space** se interpretan según las reglas siguientes (la regla **n_sep_by_space** aparece entre paréntesis):

- 0: símbolo de moneda está separado del valor por un espacio para no negativo (negativo) valor monetario con formato.

- 1 - no hay ninguna separación de espacio entre el símbolo de moneda y el valor no negativo (negativo) valor monetario con formato.

Los valores de **p_sign_posn** y **n_sign_posn** se interpretan según las reglas siguientes:

- 0 - los paréntesis rodean los símbolos de moneda y de cantidad.

- 1 - la cadena de signo precede a símbolos de moneda y de cantidad.

- 2 - la cadena de signo de sigue símbolos de moneda y de cantidad.

- 3 - la cadena de signo precede inmediatamente a símbolo de moneda.

- 4 - inicio de sesión de cadena inmediatamente símbolo de moneda se indica a continuación.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
