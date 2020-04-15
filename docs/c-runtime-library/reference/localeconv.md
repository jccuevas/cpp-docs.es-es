---
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: a617980d60b3a12c06b30aab6cd457792a1aa770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342141"
---
# <a name="localeconv"></a>localeconv

Obtiene información detallada sobre la configuración regional.

## <a name="syntax"></a>Sintaxis

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Valor devuelto

**localeconv** devuelve un puntero a un objeto rellenado de tipo [struct lconv](../../c-runtime-library/standard-types.md). Los valores contenidos en el objeto se copian de la configuración regional en el almacenamiento local de subprocesos y se pueden sobrescribir mediante llamadas posteriores a **localeconv**. Los cambios realizados en los valores de este objeto no modifican la configuración regional. Las llamadas a [setlocale](setlocale-wsetlocale.md) con valores de *categoría* de **LC_ALL**, **LC_MONETARY**o **LC_NUMERIC** sobrescribir el contenido de la estructura.

## <a name="remarks"></a>Observaciones

La función **localeconv** obtiene información detallada sobre el formato numérico de la configuración regional actual. Esta información se almacena en una estructura de tipo **lconv**. La estructura **lconv**, definida en LOCALE.H, contiene los miembros siguientes:

|Campo|Significado|
|-|-|
decimal_point,<br/>_W_decimal_point|Puntero al carácter de punto decimal para cantidades no monetarias.
thousands_sep,<br/>_W_thousands_sep|Puntero al carácter que separa grupos de dígitos a la izquierda del punto decimal para cantidades no monetarias.
agrupación|Puntero a un entero de tamaño **char**que contiene el tamaño de cada grupo de dígitos en cantidades no monetarias.
int_curr_symbol,<br/>_W_int_curr_symbol|Puntero al símbolo de moneda internacional para la configuración regional actual. Los tres primeros caracteres especifican el símbolo de moneda internacional alfabético como se define en el estándar *Códigos ISO 4217 para la representación de las monedas y tipos de fondos*. El cuarto carácter (inmediatamente antes del carácter nulo) separa el símbolo de moneda internacional de la cantidad de moneda.
Currency_symbol<br/>_W_currency_symbol|Puntero al símbolo de moneda local para la configuración regional actual.
mon_decimal_point,<br/>_W_mon_decimal_point|Puntero al carácter decimal para cantidades monetarias.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Puntero al separador para grupos de dígitos a la izquierda de decimal en cantidades monetarias.
mon_grouping|Puntero a un entero de tamaño **char**que contiene el tamaño de cada grupo de dígitos en cantidades monetarias.
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

Excepto como se especifica, los miembros `char *` de `wchar_t *` la estructura **lconv** que tienen y versiones son punteros a cadenas. Cualquiera de estos que sea igual a **""** (o **L""** para **wchar_t** <strong>\*</strong>) es de longitud cero o no se admite en la configuración regional actual. Tenga en cuenta que **decimal_point** y **_W_decimal_point** siempre son compatibles y de longitud distinta de cero.

Los miembros **char** de la estructura son números no negativos pequeños, no caracteres. Cualquiera de estos que sea igual a **CHAR_MAX** no se admite en la configuración regional actual.

Los valores de **agrupación** y **mon_grouping** se interpretan de acuerdo con las siguientes reglas:

- **CHAR_MAX** - No realice ninguna agrupación adicional.

- 0 - Utilice el elemento anterior para cada uno de los dígitos restantes.

- *n* - Número de dígitos que componen el grupo actual. Se examina el siguiente elemento para determinar el tamaño del siguiente grupo de dígitos antes del grupo actual.

Los valores de **int_curr_symbol** se interpretan según las reglas siguientes:

- Los tres primeros caracteres especifican el símbolo de moneda internacional alfabético como se define en el estándar *Códigos ISO 4217 para la representación de las monedas y tipos de fondos*.

- El cuarto carácter (inmediatamente antes del carácter nulo) separa el símbolo de moneda internacional de la cantidad de moneda.

Los valores de **p_cs_precedes** y **n_cs_precedes** se interpretan según las reglas siguientes (la regla **n_cs_precedes** aparece entre paréntesis):

- 0 - El símbolo de moneda sigue el valor del valor monetario no negativo (negativo).

- 1 - El símbolo de moneda precede al valor del valor monetario no negativo (negativo).

Los valores de **p_sep_by_space** y **n_sep_by_space** se interpretan según las reglas siguientes (la regla **n_sep_by_space** aparece entre paréntesis):

- 0 - El símbolo de moneda está separado del valor por espacio para el valor monetario no negativo (negativo).

- 1 - No hay separación de espacio entre el símbolo de moneda y el valor para el valor monetario no negativo (negativo).

Los valores de **p_sign_posn** y **n_sign_posn** se interpretan según las reglas siguientes:

- 0 - Paréntesis rodean la cantidad y el símbolo de moneda.

- 1 - La cadena de signo precede a la cantidad y al símbolo de moneda.

- 2 - La cadena de signo sigue la cantidad y el símbolo de moneda.

- 3 - La cadena de signo precede inmediatamente al símbolo de moneda.

- 4 - La cadena de signo sigue inmediatamente el símbolo de moneda.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Consulte también

[Configuración regional](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Funciones strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
