---
title: "Configuraci&#243;n regional | Microsoft Docs"
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
  - "c.international"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "información de país"
  - "rutinas de información de idioma"
  - "rutinas de configuración regional"
  - "adaptación, configuración regional"
  - "setlocale (función)"
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Configuraci&#243;n regional
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

*Locale* hace referencia a los valores de país o región y de idioma que se pueden usar para personalizar un programa.  Entre las categorías dependientes de la configuración regional se encuentran los formatos de presentación de fechas y de valores de moneda.  Para obtener más información, vea [Categorías de configuración regional](../c-runtime-library/locale-categories.md).  
  
 Use la función [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para cambiar o consultar parte de la información, o toda ella, de configuración regional del programa o subproceso actual, mientras usa funciona sin el sufijo `_l`.  Las funciones con el sufijo `_l` usan el parámetro de configuración regional que se pasa para la información de configuración regional solo durante la ejecución de esa función concreta.  Para crear una configuración regional y usarla con una función que tenga el sufijo `_l`, use [\_create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md).  Para liberar esta configuración regional, use [\_free\_locale](../c-runtime-library/reference/free-locale.md).  Para obtener la configuración regional actual, use [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md).  
  
 Use [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md) para determinar si cada subproceso tiene su propia configuración regional o todos los subprocesos de un programa comparten la misma configuración regional.  Para obtener más información, vea [Configuraciones regionales y páginas de códigos](../text/locales-and-code-pages.md).  
  
 Existen versiones más seguras de las funciones de la tabla siguiente, que se indican mediante el sufijo `_s` \(“segura”\).  Para obtener más información, vea [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
### Rutinas dependientes de la configuración regional  
  
|Rutina|Utilice|dependencia de configuración de categorías `setlocale`|  
|------------|-------------|------------------------------------------------------------|  
|[atof, \_atof\_l, \_wtof, \_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Convierte el carácter en valor de punto flotante|`LC_NUMERIC`|  
|[atoi, \_atoi\_l, \_wtoi, \_wtoi\_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Convierte el carácter en valor entero|`LC_NUMERIC`|  
|[\_atoi64, \_atoi64\_l, \_wtoi64, \_wtoi64\_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Convierte el carácter en valor entero de 64 bits|`LC_NUMERIC`|  
|[atol, \_atol\_l, \_wtol, \_wtol\_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Convierte el carácter en valor long|`LC_NUMERIC`|  
|[\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Convierte el carácter en valor double\-long|`LC_NUMERIC`|  
|[is Routines](../c-runtime-library/is-isw-routines.md)|Comprueba un entero dado para determinar si cumple una condición concreta|`LC_CTYPE`|  
|[isleadbyte, \_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Comprueba si se trata de un byte inicial|`LC_CTYPE`|  
|[localeconv](../c-runtime-library/reference/localeconv.md)|Lee los valores adecuados para dar formato a cantidades numéricas|`LC_MONETARY, LC_NUMERIC`|  
|[MB\_CUR\_MAX](../c-runtime-library/mb-cur-max.md)|Longitud máxima en bytes de cualquier carácter multibyte en la configuración regional actual \(macro definida en STDLIB.H\)|`LC_CTYPE`|  
|[\_mbccpy, \_mbccpy\_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[\_mbccpy\_s, \_mbccpy\_s\_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Copia un carácter multibyte|`LC_CTYPE`|  
|[\_mbclen, mblen, \_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Valida y devuelve el número de bytes del carácter multibyte|`LC_CTYPE`|  
|[strlen, wcslen, \_mbslen, \_mbslen\_l, \_mbstrlen, \_mbstrlen\_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|En el caso de cadenas de caracteres multibyte: valida cada carácter de la cadena; devuelve la longitud de la cadena|`LC_CTYPE`|  
|[mbstowcs, \_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convierte la secuencia de caracteres multibyte en la secuencia correspondiente de caracteres anchos|`LC_CTYPE`|  
|[mbtowc, \_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convierte el carácter multibyte en el carácter ancho correspondiente|`LC_CTYPE`|  
|Funciones [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|Escribe resultados con formato|`LC_NUMERIC` \(determina la salida de caracteres de base\)|  
|Funciones [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|Lee la entrada con formato|`LC_NUMERIC` \(determina el reconocimiento de caracteres de base\)|  
|[setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|Selecciona la configuración regional del programa|No es aplicable|  
|[strcoll, wcscoll, \_mbscoll, \_strcoll\_l, \_wcscoll\_l, \_mbscoll\_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Compara los caracteres de dos cadenas|`LC_COLLATE`|  
|[\_stricmp, \_wcsicmp, \_mbsicmp, \_stricmp\_l, \_wcsicmp\_l, \_mbsicmp\_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Compara dos cadenas sin distinción entre mayúsculas y minúsculas|`LC_CTYPE`|  
|[\_stricoll, \_wcsicoll, \_mbsicoll, \_stricoll\_l, \_wcsicoll\_l, \_mbsicoll\_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Compara los caracteres de dos cadenas sin distinción entre mayúsculas y minúsculas|`LC_COLLATE`|  
|[\_strncoll, \_wcsncoll, \_mbsncoll, \_strncoll\_l, \_wcsncoll\_l, \_mbsncoll\_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Compara los primeros `n` caracteres de dos cadenas|`LC_COLLATE`|  
|[\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Compara los caracteres de dos cadenas sin distinción entre mayúsculas y minúsculas|`LC_CTYPE`|  
|[\_strnicoll, \_wcsnicoll, \_mbsnicoll, \_strnicoll\_l, \_wcsnicoll\_l, \_mbsnicoll\_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Compara los primeros `n` caracteres de dos cadenas sin distinción entre mayúsculas y minúsculas|`LC_COLLATE`|  
|[strftime, wcsftime, \_strftime\_l, \_wcsftime\_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Da formato al valor de fecha y hora de acuerdo con el argumento `format` proporcionado|`LC_TIME`|  
|[\_strlwr, \_wcslwr, \_mbslwr, \_strlwr\_l, \_wcslwr\_l, \_mbslwr\_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md),[\_strlwr\_s, \_strlwr\_s\_l, \_mbslwr\_s, \_mbslwr\_s\_l, \_wcslwr\_s, \_wcslwr\_s\_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Convierte, en contexto, cada mayúscula de la cadena especificada en minúscula|`LC_CTYPE`|  
|[strtod, \_strtod\_l, wcstod, \_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Convierte el valor de cadena en valor `double`|`LC_NUMERIC` \(determina el reconocimiento de caracteres de base\)|  
|[strtol, wcstol, \_strtol\_l, \_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Convierte el valor de cadena en valor `long`|`LC_NUMERIC` \(determina el reconocimiento de caracteres de base\)|  
|[strtoul, \_strtoul\_l, wcstoul, \_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Convierte la cadena de caracteres en valor long sin signo|`LC_NUMERIC` \(determina el reconocimiento de caracteres de base\)|  
|[\_strupr, \_strupr\_l, \_mbsupr, \_mbsupr\_l, \_wcsupr\_l, \_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md),[\_strupr\_s, \_strupr\_s\_l, \_mbsupr\_s, \_mbsupr\_s\_l, \_wcsupr\_s, \_wcsupr\_s\_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Convierte, en contexto, cada minúscula de la cadena especificada en mayúscula|`LC_CTYPE`|  
|[strxfrm, wcsxfrm, \_strxfrm\_l, \_wcsxfrm\_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Transforma la cadena en formato intercalado según la configuración regional|`LC_COLLATE`|  
|[tolower, \_tolower, towlower, \_tolower\_l, \_towlower\_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md),[\_mbctolower, \_mbctolower\_l, \_mbctoupper, \_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Convierte el carácter dado en el carácter en minúscula correspondiente|`LC_CTYPE`|  
|[toupper, \_toupper, towupper, \_toupper\_l, \_towupper\_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md),[\_mbctolower, \_mbctolower\_l, \_mbctoupper, \_mbctoupper\_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Convierte el carácter dado en la letra mayúscula correspondiente|`LC_CTYPE`|  
|[wcstombs, \_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md),[wcstombs\_s, \_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convierte la secuencia de caracteres anchos en la secuencia correspondiente de caracteres multibyte|`LC_CTYPE`|  
|[wctomb, \_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md),[wctomb\_s, \_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convierte el carácter ancho en el carácter multibyte correspondiente|`LC_CTYPE`|  
  
> [!NOTE]
>  En el caso de las rutinas multibyte, la página de códigos multibyte debe ser equivalente a la configuración regional establecida mediante [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).  [\_setmbcp](../c-runtime-library/reference/setmbcp.md), con el argumento `_MB_CP_LOCALE`, hace que la página de códigos multibyte sea igual que la página de códigos de `setlocale`.  
  
## Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)