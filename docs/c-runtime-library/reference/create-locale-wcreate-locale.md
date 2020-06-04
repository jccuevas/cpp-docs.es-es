---
title: _create_locale, _wcreate_locale
ms.date: 4/2/2020
api_name:
- _create_locale
- __create_locale
- _wcreate_locale
- _o__create_locale
- _o__wcreate_locale
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- create_locale
- _create_locale
- __create_locale
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
ms.openlocfilehash: 31bde3d032bdb47d63db5730ba53016de573332c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912093"
---
# <a name="_create_locale-_wcreate_locale"></a>_create_locale, _wcreate_locale

Crea un objeto de configuración regional.

## <a name="syntax"></a>Sintaxis

```C
_locale_t _create_locale(
   int category,
   const char *locale
);
_locale_t _wcreate_locale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parámetros

*category*<br/>
Categoría.

*locale*<br/>
Especificador de la configuración regional.

## <a name="return-value"></a>Valor devuelto

Si se especifica una configuración *regional* y una *categoría* válidas, devuelve la configuración regional especificada como un objeto **_locale_t** . La configuración regional actual del programa no cambia.

## <a name="remarks"></a>Observaciones

La función **_create_locale** permite crear un objeto que representa determinados valores específicos de la región, para su uso en versiones específicas de la configuración regional de muchas funciones de CRT (funciones con el sufijo **_L** ). El comportamiento es similar a **setlocale**, salvo que en lugar de aplicar la configuración regional especificada al entorno actual, la configuración se guarda en una **_locale_t** estructura que se devuelve. La estructura de **_locale_t** se debe liberar mediante [_free_locale](free-locale.md) cuando ya no se necesite.

**_wcreate_locale** es una versión con caracteres anchos de **_create_locale**; el argumento de *configuración regional* para **_wcreate_locale** es una cadena de caracteres anchos. **_wcreate_locale** y **_create_locale** se comportan de manera idéntica.

El argumento *Category* especifica las partes del comportamiento específico de la configuración regional que se ven afectados. Las marcas que se usan para la *categoría* y las partes del programa a las que afectan son las siguientes:

| marca de *categoría* | Afecta a |
|-----------------|---------|
| **LC_ALL** |Todas las categorías, como se indica a continuación. |
| **LC_COLLATE** |Las funciones **strcoll (**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**y **wcsxfrm** . |
| **LC_CTYPE** | Las funciones de control de caracteres (excepto **isdigit**, **isxdigit**, **mbstowcs**y **mbtowc**, que no se ven afectadas). |
| **LC_MONETARY** | Información de formato de moneda devuelta por la función **localeconv** . |
| **LC_NUMERIC** | Carácter de separador decimal para las rutinas de salida con formato (por ejemplo, **printf**), para las rutinas de conversión de datos y para la información de formato no monetaria devuelta por **localeconv**. Además del carácter de separador decimal, **LC_NUMERIC** establece el separador de miles y la cadena de control de agrupación devueltas por [localeconv](localeconv.md). |
| **LC_TIME** | Las funciones **strftime** y **wcsftime** . |

Esta función valida los parámetros de *configuración regional* y de *categoría* . Si el parámetro de categoría no es ninguno de los valores especificados en la tabla anterior o si la *configuración regional* es **null**, la función devuelve **null**.

El argumento de *configuración regional* es un puntero a una cadena que especifica la configuración regional. Para obtener información sobre el formato del argumento de *configuración regional* , consulte [nombres de configuración regional, idiomas y cadenas de país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

El argumento de *configuración regional* puede tomar un nombre de configuración regional, una cadena de idioma, una cadena de idioma y un código de país o región, una página de códigos, una cadena de idioma, un código de país o región y una página de códigos. El conjunto de nombres de configuración regional, idiomas, códigos de país o región y páginas de códigos disponibles incluye todo lo que admiten los NLS API de Windows. El conjunto de nombres de configuración regional que admite **_create_locale** se describe en [nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). El conjunto de cadenas de idioma y de país o región que admite **_create_locale** se enumeran en cadenas de [idioma](../../c-runtime-library/language-strings.md) y [cadenas de país o región](../../c-runtime-library/country-region-strings.md).

Para obtener más información sobre la configuración regional, consulte [setlocale, _wsetlocale](setlocale-wsetlocale.md).

El nombre anterior de esta función, **__create_locale** (con dos subrayados iniciales), ha quedado en desuso.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_create_locale.c
// Sets the current locale to "de-CH" using the
// setlocale function and demonstrates its effect on the strftime
// function.

#include <stdio.h>
#include <locale.h>
#include <time.h>

int main(void)
{
    time_t ltime;
    struct tm thetime;
    unsigned char str[100];
    _locale_t locale;

    // Create a locale object representing the German (Switzerland) locale
    locale = _create_locale(LC_ALL, "de-CH");
    time (&ltime);
    _gmtime64_s(&thetime, &ltime);

    // %#x is the long date representation, appropriate to
    // the current locale
    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In de-CH locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);

    // Create a locale object representing the default C locale
    locale = _create_locale(LC_ALL, "C");
    time(&ltime);
    _gmtime64_s(&thetime, &ltime);

    if (!_strftime_l((char *)str, 100, "%#x",
                     (const struct tm *)&thetime, locale))
    {
        printf("_strftime_l failed!\n");
    }
    else
    {
        printf("In 'C' locale, _strftime_l returns '%s'\n", str);
    }

    _free_locale(locale);
}
```

```Output
In de-CH locale, _strftime_l returns 'Samstag, 9. Februar 2002'
In 'C' locale, _strftime_l returns 'Saturday, February 09, 2002'
```

## <a name="see-also"></a>Consulte también

[Nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Language Strings](../../c-runtime-library/language-strings.md)<br/>
[Cadenas de país y región](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Funciones de strcoll (](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
