---
title: Nombres de configuración regional, idiomas y cadenas de país/región
ms.date: 08/13/2018
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: 8776cdc37cc816151db6e7f441df5686da5c1ae0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601739"
---
# <a name="locale-names-languages-and-countryregion-strings"></a>Nombres de configuración regional, idiomas y cadenas de país/región

El argumento de *locale* para las funciones `setlocale` y `_create_locale` se puede establecer usando los nombres, los idiomas, los códigos de país o región, y las páginas de códigos de la configuración regional compatibles con la API NLS de Windows. El argumento de *locale* tiene el formato siguiente:

> *locale* :: "*locale_name*" &nbsp;&nbsp;&nbsp;&nbsp;| "*language*\[\_*country-region*]\[.*code_page*]]" &nbsp;&nbsp;&nbsp;&nbsp;| ".*code_page*" &nbsp;&nbsp;&nbsp;&nbsp;| "C" &nbsp;&nbsp;&nbsp;&nbsp;| "" &nbsp;&nbsp;&nbsp;&nbsp;| NULL

Se prefiere el formato de nombre de la configuración regional; por ejemplo, use `en-US` para Inglés (Estados Unidos) o `bs-Cyrl-BA` para Bosnio (cirílico, Bosnia-Herzegovina). El conjunto de nombres de configuración regional se describe en [Locale Names](/windows/desktop/Intl/locale-names)(Nombres de configuración regional). Para una lista de nombres de configuración regional compatibles con la versión del sistema operativo Windows, consulte la columna **Language tag** (Etiqueta de idioma) de la en la tabla [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx) (Apéndice A: Comportamiento del producto) en [MS-LCID]: Windows Language Code Identifier (LCID) Reference ([MS-LCID]: Referencia de identificador de configuración regional (LCID) de Windows). En este recurso se enumeran las partes de idioma, script y región compatibles de los nombres de configuración regional. Para obtener información sobre nombres de configuración regional compatibles que tienen criterios de ordenación no predeterminados, vea la columna **Locale Name** (Nombre de configuración regional) en [Sort Order Identifiers](/windows/desktop/Intl/sort-order-identifiers)(Identificadores de criterio de ordenación). En Windows 10 o posterior, se permiten los nombres de la configuración regional que corresponden a etiquetas de idioma BCP-47 válidas. Por ejemplo, `jp-US` es una etiqueta BCP-47 válida, pero es eficaz solo `US` para la funcionalidad de configuración regional.

El formato *idioma*[*_país_región*[.*página_de_códigos*]] form is stored in the locale setting for a category when a idioma string, or idioma string and country/region string, is used to create the locale. El conjunto de cadenas de idioma admitidas se describe en [Language Strings](../c-runtime-library/language-strings.md). La lista de cadenas de país o región admitidas está en [Country/Region Strings](../c-runtime-library/country-region-strings.md). Si el idioma especificado no está asociado al país o región especificados, en la configuración regional se almacena el idioma predeterminado para el país o región especificados. No se recomienda usar este formato para las cadenas de configuración regional insertadas en código o serializadas en el almacenamiento, ya que es más probable que una actualización del sistema operativo cambie estas cadenas que el formato de nombre de configuración regional.

La página de códigos es la página de códigos de ANSI/OEM asociada a la configuración regional. La página de códigos se determina automáticamente al especificar una configuración regional solo por idioma o por idioma y país o región. El valor especial `.ACP` especifica la página de códigos ANSI para el país o región. El valor especial `.OCP` especifica la página de códigos OEM para el país o región. Por ejemplo, si especifica `"Greek_Greece.ACP"` como configuración regional, la configuración regional se almacena como `Greek_Greece.1253` (página de códigos ANSI del griego); si especifica `"Greek_Greece.OCP"` como configuración regional, se almacena como `Greek_Greece.737` (página de códigos OEM del griego). Para obtener más información sobre las páginas de códigos, vea [Code Pages](../c-runtime-library/code-pages.md). Para obtener la lista de páginas de códigos admitidas en Windows, vea [Code Page Identifiers](/windows/desktop/Intl/code-page-identifiers)(Identificadores de páginas de códigos).

Si usa solo la página de códigos para especificar la configuración regional, se usan el idioma y el país o región predeterminados del usuario, según se indica en [GetUserDefaultLocaleName](/windows/desktop/api/winnls/nf-winnls-getuserdefaultlocalename). Por ejemplo, si especifica `".1254"` (ANSI del turco) como configuración regional de un usuario configurado para inglés (Estados Unidos), la configuración regional que se almacena es `English_United States.1254`. No se recomienda usar este formato, porque podría causar un comportamiento incoherente.

Un valor de argumento *locale* de `C` especifica el entorno compatible con ANSI mínimo para la conversión de C. La configuración regional de `C` da por hecho que cada tipo de datos **char** es de 1 byte y su valor es siempre menor que 256. Si *locale* señala a una cadena vacía, la configuración regional es el entorno nativo definido por la implementación.

Puede especificar a la vez todas las categorías de configuración regional para las funciones `setlocale` y `_wsetlocale` con la categoría `LC_ALL` . Todas las categorías se pueden establecer en la misma configuración regional. También puede establecer cada categoría por separado mediante un argumento de configuración regional con el siguiente formato:

> LC_ALL_specifier :: locale &nbsp;&nbsp;&nbsp;&nbsp;| [LC_COLLATE=locale][;LC_CTYPE=locale][;LC_MONETARY=locale][;LC_NUMERIC=locale][;LC_TIME=locale]

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
