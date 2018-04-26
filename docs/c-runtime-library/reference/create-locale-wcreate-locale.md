---
title: _create_locale, _wcreate_locale | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _create_locale
- __create_locale
- _wcreate_locale
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
- create_locale
- _create_locale
- __create_locale
dev_langs:
- C++
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 420f18b3bac3daf538ee5eee48b8e57bedbdf9c1
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="createlocale-wcreatelocale"></a>_create_locale, _wcreate_locale

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

Si es válido *configuración regional* y *categoría* se proporcionan, se devuelve la configuración regional especificada como un **_locale_t** objeto. La configuración regional actual del programa no cambia.

## <a name="remarks"></a>Comentarios

El **_create_locale** función le permite crear un objeto que representa ciertas configuraciones específicas de la región, para su uso en versiones específicas de la configuración regional de muchas funciones de CRT (funciones con el **_l** sufijo ). El comportamiento es similar a **setlocale**, excepto que en lugar de aplicar la configuración regional especificada en el entorno actual, la configuración se guarda en un **_locale_t** estructura que se devuelve. El **_locale_t** estructura debe liberarse mediante [_free_locale](free-locale.md) cuando ya no sea necesario.

**_wcreate_locale** es una versión con caracteres anchos de **_create_locale**; el *configuración regional* argumento pasado a **_wcreate_locale** es una cadena de caracteres anchos. **_wcreate_locale** y **_create_locale** se comportan exactamente igual.

El *categoría* argumento especifica las partes del comportamiento específico de la configuración regional que se ven afectadas. Las marcas que se usan para *categoría* y las partes del programa que afecten a son como se muestra en la tabla siguiente.

|*categoría* marca|Afecta a|
|-|-|
**LC_ALL**|Todas las categorías, como se indica a continuación.
**LC_COLLATE**|El **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_ strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**, y **wcsxfrm** funciones.
**LC_CTYPE**|Las funciones de control de caracteres (excepto **isdigit**, **isxdigit**, **mbstowcs**, y **mbtowc**, que se ven afectadas).
**LC_MONETARY**|Información de formato de moneda devuelta por la **localeconv** (función).
**LC_NUMERIC**|Carácter para las rutinas de salida con formato de punto decimal (como **printf**), para las rutinas de conversión de datos y la información de formato no monetaria devuelta por **localeconv**. Además del carácter de separador decimal, **LC_NUMERIC** separador de miles de conjuntos y el control de agrupación cadena devuelta por [localeconv](localeconv.md).
**LC_TIME**|El **strftime** y **wcsftime** funciones.

Esta función valida el *categoría* y *configuración regional* parámetros. Si el parámetro de categoría no es uno de los valores especificados en la tabla anterior o si *configuración regional* es **NULL**, la función devuelve **NULL**.

El *configuración regional* argumento es un puntero a una cadena que especifica la configuración regional. Para obtener información acerca del formato de la *configuración regional* argumento, vea [nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).

El *configuración regional* argumento puede tomar un nombre de configuración regional, una cadena de idioma, una cadena de idioma y el código de país o región, una página de códigos, o una cadena de idioma, el código de país o región y página de códigos. El conjunto de nombres de configuración regional, idiomas, códigos de país o región y páginas de códigos disponibles contiene todos los admitidos por la API NLS de Windows, excepto las páginas de códigos que requieren más de dos bytes por carácter, por ejemplo UTF-7 y UTF-8. Si se proporciona una página de códigos como UTF-7 o UTF-8, **_create_locale** se producirá un error y devolverá NULL. El conjunto de nombres de configuración regional compatibles con **_create_locale** se describen en [nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). El conjunto de cadenas de idioma y país o región admitidas por **_create_locale** se enumeran en [cadenas de idioma](../../c-runtime-library/language-strings.md) y [cadenas de país/región](../../c-runtime-library/country-region-strings.md).

Para obtener más información sobre la configuración regional, consulte [setlocale, _wsetlocale](setlocale-wsetlocale.md).

El nombre anterior de esta función, **__create_locale** (con dos caracteres de subrayado iniciales), está en desuso.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_create_locale**|\<locale.h>|
|**_wcreate_locale**|\<locale.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[Nombres de configuración regional, idiomas y cadenas de país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Cadenas de idioma](../../c-runtime-library/language-strings.md)<br/>
[Cadenas de país y región](../../c-runtime-library/country-region-strings.md)<br/>
[_free_locale](free-locale.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
