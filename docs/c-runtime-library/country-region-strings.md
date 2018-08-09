---
title: Cadenas de país y región | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f227feec25e3b487772f8e469651f08be825419f
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605635"
---
# <a name="countryregion-strings"></a>Country/Region Strings

Las cadenas de país y la región se pueden combinar con una cadena de idioma para crear una especificación de configuración regional para las funciones `setlocale`, `_wsetlocale`, `_create_locale`y `_wcreate_locale` . Para las listas de nombres de país y región son compatibles con varias versiones de sistema operativo Windows, consulte las columnas **Language** (Idioma), **Location** (Ubicación) y **Language tag** (Etiqueta de idioma) de la en la tabla [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx) (Apéndice A: Comportamiento del producto) en [MS-LCID]: Windows Language Code Identifier (LCID) Reference ([MS-LCID]: Referencia de identificador de configuración regional (LCID) de Windows). Para un ejemplo de código que enumera los nombres de configuración regional disponibles y los valores relacionados, consulte [NLS: Name-based APIs Sample](/windows/desktop/intl/nls--name-based-apis-sample) (NLS: ejemplo de API basadas en nombres).

## <a name="additional-supported-country-and-region-strings"></a>Cadenas de país y región compatibles adicionales

La implementación de la biblioteca en tiempo de ejecución de Microsoft C también admite las siguientes cadenas y abreviaturas de país o región:

|Cadena de país o región|Abreviatura|Nombre de configuración regional equivalente|
|----------------------------|------------------|----------------------------|
|america|EE. UU.|en-US|
|britain|GBR|en-GB|
|china|CHN|zh-CN|
|czech|CZE|cs-CZ|
|england|GBR|en-GB|
|great britain|GBR|en-GB|
|holland|NLD|nl-NL|
|hong-kong|HKG|zh-HK|
|new-zealand|NZL|en-NZ|
|nz|NZL|en-NZ|
|pr china|CHN|zh-CN|
|pr-china|CHN|zh-CN|
|puerto-rico|PRI|es-PR|
|slovak|SVK|sk-SK|
|south africa|ZAF|af-ZA|
|south korea|KOR|ko-KR|
|south-africa|ZAF|af-ZA|
|south-korea|KOR|ko-KR|
|trinidad & tobago|TTO|en-TT|
|uk|GBR|en-GB|
|united-kingdom|GBR|en-GB|
|united-states|EE. UU.|en-US|
|us|EE. UU.|en-US|

## <a name="see-also"></a>Vea también

[Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)  
[Cadenas de idioma](../c-runtime-library/language-strings.md)  
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)  
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)  
