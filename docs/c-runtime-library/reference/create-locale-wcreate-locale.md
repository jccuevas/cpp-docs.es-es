---
title: _create_locale, _wcreate_locale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- locales, creating
- _create_locale function
- create_locale function
- __create_locale function
ms.assetid: ca362464-9f4a-4ec6-ab03-316c55c5be81
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 73e89121dda53300b276b76f49625ad274df4519
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="createlocale-wcreatelocale"></a>_create_locale, _wcreate_locale
Crea un objeto de configuración regional.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_locale_t _create_locale(  
   int category,  
   const char *locale   
);  
_locale_t _wcreate_locale(  
   int category,  
   const wchar_t *locale   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `category`  
 Categoría.  
  
 `locale`  
 Especificador de la configuración regional.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se proporcionan parámetros `locale` y `category` válidos, devuelve la configuración regional especificada como objeto `_locale_t`. La configuración regional actual del programa no cambia.  
  
## <a name="remarks"></a>Comentarios  
 La función `_create_locale` permite crear un objeto que represente ciertos valores específicos de la región, para su uso en versiones específicas de la configuración regional de muchas funciones de CRT (funciones con el sufijo `_l`). El comportamiento es parecido al de `setlocale`, salvo que en lugar de aplicar la configuración regional especificada al entorno actual, la configuración se guarda en una estructura de `_locale_t` que se devuelve. La estructura `_locale_t` debe liberarse mediante [_free_locale](../../c-runtime-library/reference/free-locale.md) cuando ya no se necesite.  
  
 `_wcreate_locale` es una versión con caracteres anchos de `_create_locale`; el argumento `locale` para `_wcreate_locale` es una cadena de caracteres anchos. Por lo demás, `_wcreate_locale` y `_create_locale` se comportan de forma idéntica.  
  
 El argumento de `category` especifica las partes del comportamiento específico de la configuración regional que resultan afectadas. Las marcas que se usan para `category` y las partes del programa a las que afectan se muestran en la tabla siguiente.  
  
 `LC_ALL`  
 Todas las categorías, como se indica a continuación.  
  
 `LC_COLLATE`  
 Las funciones `strcoll`, `_stricoll`, `wcscoll`, `_wcsicoll`, `strxfrm`, `_strncoll`, `_strnicoll`, `_wcsncoll`, `_wcsnicoll` y `wcsxfrm`.  
  
 `LC_CTYPE`  
 Las funciones de control de caracteres (excepto `isdigit`, `isxdigit`, `mbstowcs` y `mbtowc`, que no se ven afectadas).  
  
 `LC_MONETARY`  
 Información de formato de moneda devuelta por la función `localeconv`.  
  
 `LC_NUMERIC`  
 Carácter de separador decimal para las rutinas de salida con formato (por ejemplo `printf`), para las rutinas de conversión de datos y para la información de formato no monetaria devuelta por `localeconv`. Además del carácter de separador decimal, `LC_NUMERIC` establece el separador de miles y la cadena de control de agrupación que devuelve [localeconv](../../c-runtime-library/reference/localeconv.md).  
  
 `LC_TIME`  
 Las funciones `strftime` y `wcsftime`.  
  
 Esta función valida los parámetros `category` y `locale`. Si el parámetro de categoría no es uno de los valores especificados en la tabla anterior, o si `locale` es `NULL`, la función devuelve `NULL`.  
  
 El argumento de `locale` es un puntero a una cadena que especifica la configuración regional. Para obtener información sobre el formato del argumento `locale`, consulte [Nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md).  
  
 El argumento de `locale` puede tomar un nombre de configuración regional, una cadena de idioma, una cadena de idioma y un código de país o región, una página de códigos, o una cadena de idioma, un código de país o región y una página de códigos. El conjunto de nombres de configuración regional, idiomas, códigos de país o región y páginas de códigos disponibles contiene todos los admitidos por la API NLS de Windows, excepto las páginas de códigos que requieren más de dos bytes por carácter, por ejemplo UTF-7 y UTF-8. Si proporciona una página de códigos como UTF-7 o UTF-8, `_create_locale` producirá un error y devolverá NULL. El conjunto de nombres de configuración regional que `_create_locale` admite se describe en [Nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). El conjunto de cadenas de idioma y de país/región que `_create_locale` admite se muestra en [Cadenas de idioma](../../c-runtime-library/language-strings.md) y [Cadenas de país y región](../../c-runtime-library/country-region-strings.md).  
  
 Para obtener más información sobre la configuración regional, consulte [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 El nombre anterior de esta función, `__create_locale` (con dos caracteres de subrayado iniciales), está desusado.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_create_locale`|\<locale.h>|  
|`_wcreate_locale`|\<locale.h> o \<wchar.h>|  
  
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
 [Nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Cadenas de idioma](../../c-runtime-library/language-strings.md)   
 [Cadenas de país y región](../../c-runtime-library/country-region-strings.md)   
 [_free_locale](../../c-runtime-library/reference/free-locale.md)   
 [_configthreadlocale](../../c-runtime-library/reference/configthreadlocale.md)   
 [setlocale](../../preprocessor/setlocale.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcoll (Funciones)](../../c-runtime-library/strcoll-functions.md)   
 [strftime, wcsftime, _strftime_l, _wcsftime_l](../../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)   
 [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)