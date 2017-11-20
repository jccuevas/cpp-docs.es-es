---
title: strcoll (Funciones) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords: strcoll
dev_langs: C++
helpviewer_keywords:
- code pages, using for string comparisons
- string comparison [C++], culture-specific
- strcoll functions
- strings [C++], comparing by code page
ms.assetid: c09eeff3-8aba-4cfb-a524-752436d85573
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 224c30dfbc79ab91e60f7f55f4835d3f627c454c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="strcoll-functions"></a>strcoll (Funciones)
Cada una de las funciones `strcoll` y `wcscoll` compara dos cadenas según la configuración de la categoría `LC_COLLATE` de la página de código de configuración regional actualmente en uso. Cada una de las funciones `_mbscoll` compara dos cadenas según la página de códigos multibyte actualmente en uso. Use las funciones `coll` para las comparaciones de cadenas cuando haya alguna diferencia entre el orden del juego de caracteres y el orden lexicográfico de los caracteres en la página de códigos actual y dicha diferencia influya en la comparación. Use las funciones `cmp` correspondientes para probar solo las cadenas que son iguales.  
  
### <a name="strcoll-functions"></a>strcoll (Funciones)  
  
|SBCS|Unicode|MBCS|Descripción|  
|----------|-------------|----------|-----------------|  
|[strcoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[wcscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|[_mbscoll](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Intercalar dos cadenas|  
|[_stricoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_wcsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|[_mbsicoll](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Intercalar dos cadenas (sin distinción entre mayúsculas y minúsculas)|  
|[_strncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_wcsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|[_mbsncoll](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Intercalar los primeros `count` caracteres de dos cadenas|  
|[_strnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_wcsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|[_mbsnicoll](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Intercalar los primeros `count` caracteres de dos cadenas (sin distinción entre mayúsculas y minúsculas)|  
  
## <a name="remarks"></a>Comentarios  
 Las versiones de caracteres de byte único (SBCS) de estas funciones (`strcoll`, `stricoll`, `_strncoll` y `_strnicoll`) comparan `string1` y `string2` según la configuración de la categoría `LC_COLLATE` de la configuración regional actual. Estas funciones se diferencian de las correspondientes funciones `strcmp` en que las funciones `strcoll` usan la información de la página de código de configuración regional que proporciona secuencias de intercalación. Para comparaciones de cadenas en configuraciones regionales en que el orden del juego de caracteres y el orden lexicográfico de los caracteres son diferentes, se deben usar las funciones `strcoll` en lugar de las funciones `strcmp` correspondientes. Para obtener más información sobre `LC_COLLATE`, vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 En el caso de algunas páginas de códigos y los juegos de caracteres correspondientes, el orden de los caracteres del juego de caracteres puede no ser el mismo que el orden lexicográfico de los caracteres. En la configuración regional de "C" no es así: el orden de los caracteres del juego de caracteres ASCII es igual que el orden lexicográfico de los caracteres. Sin embargo, en algunas páginas de códigos europeas, por ejemplo, el carácter “a” (valor 0x61) precede el carácter “ä” (valor 0xE4) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente. Para realizar una comparación lexicográfica en ese caso, utilice `strcoll` en lugar de `strcmp`. Como alternativa, puede usar `strxfrm` en las cadenas originales y después usar `strcmp` en las cadenas resultantes.  
  
 `strcoll`, `stricoll`, `_strncoll` y `_strnicoll` controlan automáticamente las cadenas de caracteres multibyte según la página de código de configuración regional actualmente en uso, igual que sus homólogos de carácter ancho (Unicode). Las versiones de caracteres multibyte (MBC) de estas funciones, sin embargo, intercalan las cadenas según los caracteres en función de la página de códigos multibyte actualmente en uso.  
  
 Dado que las funciones `coll` intercalan lexicográficamente las cadenas para compararlas mientras que las funciones `cmp` prueban simplemente si las cadenas, las funciones `coll` son mucho más lentas que las versiones correspondientes de `cmp`. En consecuencia, las funciones `coll` solo se deben usar cuando el orden del juego de caracteres y el orden lexicográfico de los caracteres son distintos en la página de códigos actual, y la diferencia influye en la comparación de las cadenas.  
  
## <a name="see-also"></a>Vea también  
 [Configuración regional](../c-runtime-library/locale.md)   
 [Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md)   
 [localeconv](../c-runtime-library/reference/localeconv.md)   
 [_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l](../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp, wcscmp, _mbscmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)