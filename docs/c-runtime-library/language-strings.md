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
ms.openlocfilehash: 92ad129a5703f509cfd9543497cceffae3a6e7b3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="language-strings"></a>Language Strings
Las funciones `setlocale` y `_create_locale` pueden usar los idiomas compatibles con la API NLS de Windows en sistemas operativos que no usan la página de códigos Unicode. Para obtener una lista de idiomas compatibles con la versión del sistema operativo, vea la [Referencia de la API de compatibilidad con el idioma nacional (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). La cadena de idioma puede ser cualquiera de los valores de las columnas **Idioma** y **Abreviatura de nombre de idioma** de la lista de idiomas admitidos. Para información adicional sobre compatibilidad de idioma por versión de sistema operativo, consulte [Apéndice A: Comportamiento del producto](http://msdn.microsoft.com/goglobal/bb896001.aspx) en [MS-LCID]: Referencia de identificador de configuración regional (LCID) de Windows.   
  
La implementación de la biblioteca en tiempo de ejecución de C también admite estas cadenas de idioma:  
  
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
 [Nombres de configuración regional, idiomas y cadenas de país/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Cadenas de país y región](../c-runtime-library/country-region-strings.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)