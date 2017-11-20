---
title: "Cadenas de país y región | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords: country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c250e47688e5fbcb32779d58dd8fe8973cdc96c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="countryregion-strings"></a>Country/Region Strings
Las cadenas de país y la región se pueden combinar con una cadena de idioma para crear una especificación de configuración regional para las funciones `setlocale`, `_wsetlocale`, `_create_locale`y `_wcreate_locale` . Para listas de nombres de países o regiones compatibles con varias versiones del sistema operativo Windows, consulte la [Referencia de la API de compatibilidad con el idioma nacional (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). En las listas, la cadena de país o región puede ser cualquiera de los valores de país en la columna **Configuración regional (país o región de idioma)** o cualquiera de las abreviaturas de la columna de **Abreviatura de nombre de país o región**. Para información adicional sobre compatibilidad de idioma en el sistema operativo Windows por versión, consulte [Apéndice A: Comportamiento del producto](http://msdn.microsoft.com/goglobal/bb896001.aspx) en [MS-LCID]: Referencia de identificador de configuración regional (LCID) de Windows.  
  
 La implementación de la biblioteca en tiempo de ejecución de C también admite las siguientes cadenas y abreviaturas de país o región:  
  
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