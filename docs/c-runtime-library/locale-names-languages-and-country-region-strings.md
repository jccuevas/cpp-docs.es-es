---
title: Nombres de configuración regional, idiomas y cadenas de país/región
ms.date: 12/10/2018
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: 512eb589d964da9ef8e87f4193362c739b39b4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500058"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>Nombres de configuración regional, idiomas y cadenas de país/región de UCRT

El argumento *locale* para las funciones [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md), [\_create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) y [\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) se puede establecer mediante los nombres de configuración regional, los idiomas, los códigos de país/región y las páginas de código compatibles con NLS API de Windows. El argumento de *locale* tiene el formato siguiente:

> *locale* :: "*locale-name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "*language*\[ **\_** _country-region_\[ __.__ *code-page*]]"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| " __.__ *code-page*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "C"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| NULL

La forma *locale-name* es una cadena corta estandarizada por IETF; por ejemplo, `en-US` para Inglés (Estados Unidos) o `bs-Cyrl-BA` para Bosnio (cirílico, Bosnia Herzegovina). Se prefieren estas formas. Para obtener una lista de nombres de configuración regional admitidos por la versión del sistema operativo Windows, consulte la columna de **etiqueta de idioma** de la tabla de [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx) (Apéndice A: Comportamiento del producto) en [MS-LCID]: Windows Language Code Identifier (LCID) Reference (Referencia del identificador de configuración regional [LCID] de Windows). En este recurso se enumeran las partes de idioma, script y región compatibles de los nombres de configuración regional. Para obtener información sobre nombres de configuración regional compatibles que tienen criterios de ordenación no predeterminados, vea la columna **Locale Name** (Nombre de configuración regional) en [Sort Order Identifiers](/windows/win32/Intl/sort-order-identifiers)(Identificadores de criterio de ordenación). En Windows 10 o posterior, se permiten nombres de configuración regional que corresponden a etiquetas de idioma [BCP-47](https://tools.ietf.org/html/bcp47) válidas. Por ejemplo, `jp-US` es una etiqueta BCP-47 válida, pero es eficaz solo `US` para la funcionalidad de configuración regional.

La forma *language*\[ **\_** _country-region_\[ __.__ *code-page*]] se almacena en la configuración regional de una categoría cuando se usa una cadena de idioma o una cadena de idioma y cadena de país o región para crear la configuración regional. El conjunto de cadenas de idioma admitidas se describe en [Language Strings](../c-runtime-library/language-strings.md). (Cadenas de idioma), y la lista de cadenas de país o región admitidas se muestra en [Country/Region Strings](../c-runtime-library/country-region-strings.md) (Cadenas de país o región). Si el idioma especificado no está asociado al país o la región especificados, en la configuración regional se almacena el idioma predeterminado para el país o la región especificados. No se recomienda usar este formato para las cadenas de configuración regional insertadas en código o serializadas en el almacenamiento, ya que es más probable que una actualización del sistema operativo cambie estas cadenas que el formato de nombre de configuración regional.

*code-page* es la página de códigos de ANSI/OEM asociada a la configuración regional. La página de códigos se determina automáticamente al especificar una configuración regional solo por idioma o por idioma y país o región. El valor especial `.ACP` especifica la página de códigos ANSI para el país o región. El valor especial `.OCP` especifica la página de códigos OEM para el país o región. Por ejemplo, si especifica `"Greek_Greece.ACP"` como configuración regional, la configuración regional se almacena como `Greek_Greece.1253` (página de códigos ANSI del griego); si especifica `"Greek_Greece.OCP"` como configuración regional, se almacena como `Greek_Greece.737` (página de códigos OEM del griego). Para obtener más información sobre las páginas de códigos, vea [Code Pages](../c-runtime-library/code-pages.md). Para obtener la lista de páginas de códigos admitidas en Windows, vea [Code Page Identifiers](/windows/win32/Intl/code-page-identifiers)(Identificadores de páginas de códigos).

Si usa solo la página de códigos para especificar la configuración regional, se usan el idioma y el país o región predeterminados del usuario, según se indica en [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). Por ejemplo, si especifica `".1254"` (ANSI del turco) como configuración regional de un usuario configurado para inglés (Estados Unidos), la configuración regional que se almacena es `English_United States.1254`. No se recomienda usar este formato, porque podría causar un comportamiento incoherente.

Un valor de argumento *locale* de `C` especifica el entorno compatible con ANSI mínimo para la conversión de C. La configuración regional de `C` da por hecho que cada tipo de datos **char** es de 1 byte y su valor es siempre menor que 256. Si *locale* señala a una cadena vacía, la configuración regional es el entorno nativo definido por la implementación.

Puede especificar a la vez todas las categorías de configuración regional para las funciones `setlocale` y `_wsetlocale` con la categoría `LC_ALL` . Todas las categorías se pueden establecer en la misma configuración regional. También puede establecer cada categoría por separado mediante un argumento de configuración regional con el siguiente formato:

> *LC-ALL-specifier* :: *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| \[**LC_COLLATE=** _locale_]\[ **;LC_CTYPE=** _locale_]\[ **;LC_MONETARY=** _locale_]\[ **;LC_NUMERIC=** _locale_]\[ **;LC_TIME=** _locale_]

Puede especificar varios tipos de categoría, separados por punto y coma. Los tipos de categoría que no se especifican usan la configuración regional actual. Por ejemplo, este fragmento de código establece la configuración regional actual para todas las categorías en `de-DE`y, a continuación, establece las categorías `LC_MONETARY` en `en-GB` y `LC_TIME` en `es-ES`:

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>Vea también

[Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[Cadenas de idioma](../c-runtime-library/language-strings.md)<br/>
[Country/Region Strings](../c-runtime-library/country-region-strings.md)
