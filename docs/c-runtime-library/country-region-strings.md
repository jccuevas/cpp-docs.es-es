---
title: Cadenas de país y región
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 8556e005618a1b69c47498a07e218284dcb1164f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443438"
---
# <a name="countryregion-strings"></a>Country/Region Strings

Las cadenas de país y la región se pueden combinar con una cadena de idioma para crear una especificación de configuración regional para las funciones `setlocale`, `_wsetlocale`, `_create_locale`y `_wcreate_locale` . Para las listas de nombres de país y región son compatibles con varias versiones de sistema operativo Windows, consulte las columnas **Language** (Idioma), **Location** (Ubicación) y **Language tag** (Etiqueta de idioma) de la en la tabla [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx) (Apéndice A: Comportamiento del producto) en [MS-LCID]: Windows Language Code Identifier (LCID) Reference ([MS-LCID]: Referencia de identificador de configuración regional (LCID) de Windows). Para un ejemplo de código que enumera los nombres de configuración regional disponibles y los valores relacionados, consulte [NLS: Name-based APIs Sample](/windows/win32/intl/nls--name-based-apis-sample) (NLS: ejemplo de API basadas en nombres).

## <a name="additional-supported-country-and-region-strings"></a>Cadenas de país y región compatibles adicionales

La implementación de la biblioteca en tiempo de ejecución de Microsoft C también admite las siguientes cadenas y abreviaturas de país o región:

|Cadena de país o región|Abreviatura|Nombre de configuración regional equivalente|
|----------------------------|------------------|----------------------------|
|america|EE. UU.|es-ES|
|britain|GBR|en-GB|
|china|CHN|zh-CN|
|checo|CZE|cs-CZ|
|england|GBR|en-GB|
|great britain|GBR|en-GB|
|holland|NLD|nl-NL|
|hong-kong|HKG|zh-HK|
|new-zealand|NZL|en-NZ|
|nz|NZL|en-NZ|
|pr china|CHN|zh-CN|
|pr-china|CHN|zh-CN|
|puerto-rico|PRI|es-PR|
|eslovaco|SVK|sk-SK|
|south africa|ZAF|af-ZA|
|south korea|KOR|ko-KR|
|south-africa|ZAF|af-ZA|
|south-korea|KOR|ko-KR|
|trinidad & tobago|TTO|en-TT|
|uk|GBR|en-GB|
|united-kingdom|GBR|en-GB|
|united-states|EE. UU.|es-ES|
|americana|EE. UU.|es-ES|

## <a name="see-also"></a>Consulte también

[Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Cadenas de idioma](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
