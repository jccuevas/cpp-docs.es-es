---
title: "Cadenas de pa&#237;s y regi&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.strings"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "país/región (cadenas)"
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Cadenas de pa&#237;s y regi&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las cadenas de país y la región se pueden combinar con una cadena de idioma para crear una especificación de configuración regional para las funciones `setlocale`, `_wsetlocale`, `_create_locale` y `_wcreate_locale`. En el caso de las listas de nombres de país o región compatibles con las distintas versiones del sistema operativo Windows, vea [Referencia de la API de NLS \(compatibilidad con el idioma nacional\)](http://msdn.microsoft.com/goglobal/bb896001.aspx). En las listas, la cadena de país o región puede ser cualquiera de los valores de país de la columna **Configuración regional \(país o región de idioma\)**, o cualquiera de las abreviaturas de la columna de **Abreviatura de nombre de país o región**.  
  
 La implementación de la biblioteca en tiempo de ejecución de C también admite las siguientes cadenas y abreviaturas de país o región:  
  
|Cadena de país o región|Abreviatura|Nombre de configuración regional equivalente|  
|-----------------------------|-----------------|--------------------------------------------------|  
|america|EE. UU.|en\-US|  
|britain|GBR|en\-GB|  
|china|CHN|zh\-CN|  
|czech|CZE|cs\-CZ|  
|england|GBR|en\-GB|  
|great britain|GBR|en\-GB|  
|holland|NLD|nl\-NL|  
|hong\-kong|HKG|zh\-HK|  
|new\-zealand|NZL|en\-NZ|  
|nz|NZL|en\-NZ|  
|pr china|CHN|zh\-CN|  
|pr\-china|CHN|zh\-CN|  
|puerto\-rico|PRI|es\-PR|  
|slovak|SVK|sk\-SK|  
|south africa|ZAF|af\-ZA|  
|south korea|KOR|ko\-KR|  
|south\-africa|ZAF|af\-ZA|  
|south\-korea|KOR|ko\-KR|  
|trinidad & tobago|TTO|en\-TT|  
|uk|GBR|en\-GB|  
|united\-kingdom|GBR|en\-GB|  
|united\-states|EE. UU.|en\-US|  
|us|EE. UU.|en\-US|  
  
## Vea también  
 [Nombres de configuración regional, idiomas y cadenas de país\/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Cadenas de idioma](../c-runtime-library/language-strings.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)