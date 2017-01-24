---
title: "strcoll (Funciones) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "strcoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "páginas de códigos, usar para comparaciones de cadenas"
  - "strcoll (función)"
  - "comparación de cadenas [C++], específicas de referencias culturales"
  - "cadenas [C++], comparar por página de códigos"
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcoll (Funciones)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada una de las funciones de `strcoll` y de `wcscoll` compara dos cadenas según el valor de la categoría de `LC_COLLATE` de la página de códigos de la configuración regional actualmente en uso.  Cada una de las funciones de `_mbscoll` compara dos cadenas según la página de códigos multibyte actualmente en uso.  Utilice las funciones de `coll` para las comparaciones de cadenas cuando existe una diferencia entre el juego de caracteres petición y el carácter lexicográfico orden en la página de códigos actual y esta diferencia de interés para la comparación.  Utilice las funciones correspondientes de `cmp` para probar únicamente para la igualdad de la cadena.  
  
### funciones de strcoll  
  
|SBCS|Unicode|MBCS|Descripción|  
|----------|-------------|----------|-----------------|  
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[\_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Collate dos cadenas|  
|[\_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[\_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[\_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Collate dos cadenas \(sin distinción entre mayúsculas y minúsculas\)|  
|[\_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[\_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[\_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Collate los primeros caracteres de `count` de dos cadenas|  
|[\_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[\_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[\_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Collate los primeros caracteres de `count` de dos cadenas \(sin distinción entre mayúsculas y minúsculas\)|  
  
## Comentarios  
 Las versiones de \(SBCS\) de caracteres de solo\- byte de estas funciones \(`strcoll`, `stricoll`, `_strncoll`, y `_strnicoll`\) se comparan `string1` y `string2` según el valor de la categoría de `LC_COLLATE` de la configuración regional actual.  Estas funciones se diferencian de las funciones correspondientes de `strcmp` en que las funciones de `strcoll` utilizan la información de página de códigos de la configuración regional que proporciona secuencias de ordenación.  Para las comparaciones de cadenas en configuraciones regionales en las que el juego de caracteres order y difiere el orden lexicográfico de caracteres, las funciones de `strcoll` se deben utilizar en lugar de las funciones correspondientes de `strcmp` .  Para obtener más información sobre `LC_COLLATE`, vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 Para algunas páginas de códigos y juegos de caracteres correspondientes, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico de caracteres.  En la configuración regional de "C" no es así: el orden de los caracteres del juego de caracteres ASCII es igual que el orden lexicográfico de los caracteres.  Sin embargo, en algunas páginas de códigos europeas, por ejemplo, el carácter “a” \(valor 0x61\) precede el carácter “ä” \(valor 0xE4\) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente.  Para realizar una comparación lexicográfica en una instancia de, utilice `strcoll` en lugar de `strcmp`.  Alternativamente, puede utilizar `strxfrm` en cadenas originales, utiliza `strcmp` en las cadenas resultantes.  
  
 `strcoll`, `stricoll`, `_strncoll`, y de `_strnicoll` cadenas de multibyte\- carácter ID automáticamente según la página de códigos de la configuración regional actualmente en uso, al igual que sus homólogos de caracteres anchos \(Unicode\).  Las versiones de \(MBCS\) de multibyte\- carácter de estas funciones, sin embargo, intercalan cadenas de caracteres de la página de códigos multibyte actualmente en uso.  
  
 Dado que las funciones `coll` intercalan lexicográficamente las cadenas para compararlas mientras que las funciones `cmp` prueban simplemente si las cadenas, las funciones `coll` son mucho más lentas que las versiones correspondientes de `cmp`.  Por consiguiente, las funciones de `coll` deben utilizar cuando existe una diferencia entre el juego de caracteres petición y el carácter lexicográfico orden en la página de códigos actual y esta diferencia de interés para la comparación de cadenas.  
  
## Vea también  
 [Configuración regional](../c-runtime-library/locale.md)   
 [Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [\_mbsnbcoll, \_mbsnbcoll\_l, \_mbsnbicoll, \_mbsnbicoll\_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp, wcscmp, \_mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm, wcsxfrm, \_strxfrm\_l, \_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)