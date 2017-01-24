---
title: "Cadenas de idioma | Microsoft Docs"
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
  - "idioma (cadenas)"
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Cadenas de idioma
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las funciones `setlocale` y `_create_locale` pueden usar los idiomas compatibles con la API NLS de Windows en sistemas operativos que no usan la página de códigos Unicode.  Para obtener una lista de idiomas compatibles con la versión del sistema operativo, vea [Referencia de la API de compatibilidad con el idioma nacional \(NLS\)](http://msdn.microsoft.com/goglobal/bb896001.aspx).  La cadena de idioma puede ser cualquiera de los valores de las columnas **Idioma** y **Abreviatura de nombre de idioma** de la lista de idiomas admitidos.  La implementación de la biblioteca en tiempo de ejecución de C también admite estas cadenas de idioma:  
  
|Cadena de idioma|Nombre de configuración regional equivalente|  
|----------------------|--------------------------------------------------|  
|estadounidense|en\-US|  
|inglés de Estados Unidos|en\-US|  
|inglés\-Estados Unidos|en\-US|  
|australiano|en\-AU|  
|belga|nl\-BE|  
|canadiense|en\-CA|  
|chh|zh\-HK|  
|chi|zh\-SG|  
|chino|zh|  
|chino \(Hong Kong RAE\)|zh\-HK|  
|chino simplificado|zh\-CN|  
|chino \(Singapur\)|zh\-SG|  
|chino tradicional|zh\-TW|  
|neerlandés \(Bélgica\)|nl\-BE|  
|Estados Unidos\-inglés|en\-US|  
|inglés australiano|en\-AU|  
|inglés \(Belice\)|en\-BZ|  
|inglés \(Canadá\)|en\-CA|  
|inglés \(Caribe\)|en\-029|  
|inglés \(Irlanda\)|en\-IE|  
|inglés \(Jamaica\)|en\-JM|  
|inglés \(Nueva Zelanda\)|en\-NZ|  
|inglés \(Sudáfrica\)|en\-ZA|  
|inglés \(Trinidad y Tobago\)|en\-TT|  
|inglés \(Reino Unido\)|en\-GB|  
|inglés \(Estados Unidos\)|en\-US|  
|inglés \(USA\)|en\-US|  
|francés \(Bélgica\)|fr\-BE|  
|francés \(Canadá\)|fr\-CA|  
|francés \(Luxemburgo\)|fr\-LU|  
|francés \(Suiza\)|fr\-CH|  
|alemán \(Austria\)|de\-AT|  
|alemán \(Liechtenstein\)|de\-LI|  
|alemán \(Luxemburgo\)|de\-LU|  
|alemán \(Suiza\)|de\-CH|  
|irlandés\-inglés|en\-IE|  
|italiano \(Suiza\)|it\-CH|  
|noruego|no|  
|noruego \(Bokmal\)|nb\-NO|  
|noruego \(Nynorsk\)|nn\-NO|  
|portugués \(Brasil\)|pt\-BR|  
|español \(Argentina\)|es\-AR|  
|español \(Bolivia\)|es\-BO|  
|español \(Chile\)|es\-CL|  
|español \(Colombia\)|es\-CO|  
|español \(Costa Rica\)|es\-CR|  
|español \(República Dominicana\)|es\-DO|  
|español \(Ecuador\)|es\-EC|  
|español \(El Salvador\)|es\-SV|  
|español \(Guatemala\)|es\-GT|  
|español \(Honduras\)|es\-HN|  
|español \(México\)|es\-MX|  
|español \(alfab. internacional\)|es\-ES|  
|español \(Nicaragua\)|es\-NI|  
|español \(Panamá\)|es\-PA|  
|español \(Paraguay\)|es\-PY|  
|español \(Perú\)|es\-PE|  
|español \(Puerto Rico\)|es\-PR|  
|español \(Uruguay\)|es\-UY|  
|español \(Venezuela\)|es\-VE|  
|sueco \(Finlandia\)|sv\-FI|  
|suizo|de\-CH|  
|uk|en\-GB|  
|us|en\-US|  
|usa|en\-US|  
  
## Vea también  
 [Nombres de configuración regional, idiomas y cadenas de país\/región](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Cadenas de país y región](../c-runtime-library/country-region-strings.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale, \_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)