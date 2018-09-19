---
title: Cadenas de idioma | Microsoft Docs
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
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bcb9d5dbadc0fbaa33a3c8df6f9193704514e0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46083293"
---
# <a name="language-strings"></a>Language Strings

Las funciones [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) y [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) pueden usar los idiomas compatibles con la API NLS de Windows en sistemas operativos que no usan la página de códigos Unicode. Para una lista de idiomas compatibles con la versión del sistema operativo, consulte [Appendix A: Product Behavior](https://msdn.microsoft.com/library/cc233982.aspx) (Apéndice A: Comportamiento del producto) en [MS-LCID]: Windows Language Code Identifier (LCID) Reference. ([MS-LCID]: Referencia de identificador de configuración regional (LCID) de Windows). La cadena de idioma puede ser cualquiera de los valores de las columnas **Language** (Idioma) y **Language tag** (Etiqueta de idioma) de la lista de idiomas admitidos. Para un ejemplo de código que enumera los nombres de configuración regional disponibles y los valores relacionados, consulte [NLS: Name-based APIs Sample](/windows/desktop/intl/nls--name-based-apis-sample) (NLS: ejemplo de API basadas en nombres).

## <a name="additional-supported-language-strings"></a>Cadenas de idioma compatibles adicionales

La implementación de la biblioteca en tiempo de ejecución de Microsoft C también admite estas cadenas de idioma:

|Cadena de idioma|Nombre de configuración regional equivalente|
|---------------------|----------------------------|
|estadounidense|en-US|
|inglés de Estados Unidos|en-US|
|inglés-Estados Unidos|en-US|
|australiano|en-AU|
|belga|nl-BE|
|canadiense|en-CA|
|chh|zh-HK|
|chi|zh-sg|
|chino|zh|
|chino (Hong Kong RAE)|zh-HK|
|chino simplificado|zh-CN|
|chino (Singapur)|zh-sg|
|chino tradicional|zh-TW|
|neerlandés (Bélgica)|nl-BE|
|Estados Unidos-inglés|en-US|
|inglés australiano|en-AU|
|inglés (Belice)|en-BZ|
|inglés (Canadá)|en-CA|
|inglés (Caribe)|en-029|
|inglés (Irlanda)|en-IE|
|inglés (Jamaica)|en-JM|
|inglés (Nueva Zelanda)|en-NZ|
|inglés (Sudáfrica)|en-ZA|
|inglés (Trinidad y Tobago)|en-TT|
|inglés (Reino Unido)|en-GB|
|inglés (Estados Unidos)|en-US|
|inglés (USA)|en-US|
|francés (Bélgica)|fr-BE|
|francés (Canadá)|fr-CA|
|francés (Luxemburgo)|fr-LU|
|francés (Suiza)|fr-CH|
|alemán (Austria)|de-AT|
|alemán (Liechtenstein)|de-LI|
|alemán (Luxemburgo)|de-LU|
|alemán (Suiza)|de-CH|
|irlandés-inglés|en-IE|
|italiano (Suiza)|it-CH|
|noruego|No|
|noruego (Bokmal)|nb-NO|
|noruego (Nynorsk)|nn-NO|
|portugués (Brasil)|pt-BR|
|español (Argentina)|es-AR|
|español (Bolivia)|es-BO|
|español (Chile)|es-CL|
|español (Colombia)|es-CO|
|español (Costa Rica)|es-CR|
|español (República Dominicana)|es-DO|
|español (Ecuador)|es-EC|
|español (El Salvador)|es-SV|
|español (Guatemala)|es-GT|
|español (Honduras)|es-HN|
|español (México)|es-MX|
|español (alfab. internacional)|es-ES|
|español (Nicaragua)|es-NI|
|español (Panamá)|es-PA|
|español (Paraguay)|es-PY|
|español (Perú)|es-PE|
|español (Puerto Rico)|es-PR|
|español (Uruguay)|es-UY|
|español (Venezuela)|es-VE|
|sueco (Finlandia)|sv-FI|
|suizo|de-CH|
|uk|en-GB|
|us|en-US|
|usa|en-US|

## <a name="see-also"></a>Vea también

[Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Cadenas de país y región](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)
