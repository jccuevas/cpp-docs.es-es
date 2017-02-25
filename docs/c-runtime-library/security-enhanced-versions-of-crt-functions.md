---
title: "Versiones de funciones de CRT con seguridad mejorada | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRT, mejoras de seguridad"
  - "seguridad [CRT]"
  - "CRT con seguridad mejorada"
ms.assetid: f87e5a01-4cb2-4379-9e8f-d4693828c55a
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# Versiones de funciones de CRT con seguridad mejorada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Hay disponibles versiones más seguras de rutinas de biblioteca en tiempo de ejecución. Para obtener información más detallada sobre las mejoras de seguridad en CRT, vea [Características de seguridad de CRT](../c-runtime-library/security-features-in-the-crt.md).  
  
 **Funciones seguras**  
  
|Función de CRT|Función de seguridad mejorada|Uso|  
|--------------------|-----------------------------------|---------|  
|[\_access, \_waccess](../c-runtime-library/reference/access-waccess.md)|[\_access\_s, \_waccess\_s](../c-runtime-library/reference/access-s-waccess-s.md)|Determinar el permiso de acceso a archivos|  
|[\_alloca](../c-runtime-library/reference/alloca.md)|[\_malloca](../c-runtime-library/reference/malloca.md)|Asignar memoria en la pila|  
|[asctime, \_wasctime](../c-runtime-library/reference/asctime-wasctime.md)|[asctime\_s, \_wasctime\_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|Convertir la hora de tipo `struct tm` a cadena de caracteres|  
|[bsearch](../c-runtime-library/reference/bsearch.md)|[bsearch\_s](../c-runtime-library/reference/bsearch-s.md)|Realizar una búsqueda binaria de una matriz ordenada|  
|Función obsoleta|[\_cgets\_s, \_cgetws\_s](../c-runtime-library/reference/cgets-s-cgetws-s.md)|Obtener una cadena de caracteres de la consola|  
|[\_chsize](../c-runtime-library/reference/chsize.md)|[\_chsize\_s](../c-runtime-library/reference/chsize-s.md)|Cambiar el tamaño de un archivo|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|[clearerr\_s](../c-runtime-library/reference/clearerr-s.md)|Restablecer el indicador de error de un flujo|  
|[\_control87, \_controlfp, \_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[\_controlfp\_s](../c-runtime-library/reference/controlfp-s.md)|Obtener y establecer la palabra de control de punto flotante.|  
|[\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[\_cprintf\_s, \_cprintf\_s\_l, \_cwprintf\_s, \_cwprintf\_s\_l](../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)|Dar formato e imprimir en la consola|  
|[\_cscanf, \_cscanf\_l, \_cwscanf, \_cwscanf\_l](../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)|[\_cscanf\_s, \_cscanf\_s\_l, \_cwscanf\_s, \_cwscanf\_s\_l](../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)|Leer datos con formato de la consola|  
|[ctime, \_ctime32, \_ctime64, \_wctime, \_wctime32, \_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)|[\_ctime\_s, \_ctime32\_s, \_ctime64\_s, \_wctime\_s, \_wctime32\_s, \_wctime64\_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|Convertir la hora de tipo `time_t`, `__time32_t` o `__time64_t` a cadena de caracteres|  
|[\_ecvt](../c-runtime-library/reference/ecvt.md)|[\_ecvt\_s](../c-runtime-library/reference/ecvt-s.md)|Convertir un número `double` en una cadena|  
|[\_fcvt](../c-runtime-library/reference/fcvt.md)|[\_fcvt\_s](../c-runtime-library/reference/fcvt-s.md)|Convertir un número de punto flotante en una cadena|  
|[fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md)|[fopen\_s, \_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)|Abrir un archivo|  
|[fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[fprintf\_s, \_fprintf\_s\_l, fwprintf\_s, \_fwprintf\_s\_l](../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)|Imprimir datos con formato en un flujo|  
|[fread](../c-runtime-library/reference/fread.md)|[fread\_s](../c-runtime-library/reference/fread-s.md)|Leer de un archivo|  
|[\_fread\_nolock](../c-runtime-library/reference/fread-nolock.md)|[\_fread\_nolock\_s](../c-runtime-library/reference/fread-nolock-s2.md)|Leer de un archivo sin usar un bloqueo de escritura multiproceso|  
|[freopen, \_wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)|[freopen\_s, \_wfreopen\_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)|Volver a abrir el archivo|  
|[fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)|[fscanf\_s, \_fscanf\_s\_l, fwscanf\_s, \_fwscanf\_s\_l](../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)|Leer datos con formato de un flujo|  
|[\_ftime, \_ftime32, \_ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)|[\_ftime\_s, \_ftime32\_s, \_ftime64\_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|Obtener la hora actual|  
|[\_gcvt](../c-runtime-library/reference/gcvt.md)|[\_gcvt\_s](../c-runtime-library/reference/gcvt-s.md)|Convertir un valor de punto flotante en una cadena y almacenarlo en un búfer|  
|[getenv, \_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)|[getenv\_s, \_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|Obtiene un valor del entorno actual.|  
|Función obsoleta|[gets\_s, \_getws\_s](../c-runtime-library/reference/gets-s-getws-s.md)|Obtener una línea del flujo de `stdin`|  
|[gmtime, \_gmtime32, \_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)|[\_gmtime32\_s, \_gmtime64\_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|Convertir hora del tipo `time_t` a `struct``tm` o del tipo `__time64_t` a `struct tm`|  
|[\_itoa, \_i64toa, \_ui64toa, \_itow, \_i64tow, \_ui64tow](../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)|[\_itoa\_s, \_i64toa\_s, \_ui64toa\_s, \_itow\_s, \_i64tow\_s, \_ui64tow\_s](../c-runtime-library/reference/itoa-s-i64toa-s-ui64toa-s-itow-s-i64tow-s-ui64tow-s.md)|Convertir un entero en cadena|  
|[\_lfind](../c-runtime-library/reference/lfind.md)|[\_lfind\_s](../c-runtime-library/reference/lfind-s.md)|Realizar una búsqueda lineal de la clave especificada|  
|[localtime, \_localtime32, \_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)|[localtime\_s, \_localtime32\_s, \_localtime64\_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|Convertir la hora de tipo `time_t` a `struct tm` o del tipo `__time64_t` a `struct tm`con corrección local|  
|[\_lsearch](../c-runtime-library/reference/lsearch.md)|[\_lsearch\_s](../c-runtime-library/reference/lsearch-s.md)|Realizar una búsqueda lineal de un valor; se agrega al final de la lista si no se encuentra|  
|[\_ltoa, \_ltow](../c-runtime-library/reference/ltoa-ltow.md)|[\_ltoa\_s, \_ltow\_s](../c-runtime-library/reference/ltoa-s-ltow-s.md)|Convertir un entero largo en cadena|  
|[\_makepath, \_wmakepath](../c-runtime-library/reference/makepath-wmakepath.md)|[\_makepath\_s, \_wmakepath\_s](../c-runtime-library/reference/makepath-s-wmakepath-s.md)|Crear un nombre de ruta de acceso de componentes|  
|[\_mbccpy, \_mbccpy\_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md)|[\_mbccpy\_s, \_mbccpy\_s\_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Copiar un carácter multibyte de una cadena a otra|  
|[\_mbsnbcat, \_mbsnbcat\_l](../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)|[\_mbsnbcat\_s, \_mbsnbcat\_s\_l](../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)|Anexar, como máximo, los primeros `n` bytes de una cadena de caracteres multibyte en otra.|  
|[\_mbsnbcpy, \_mbsnbcpy\_l](../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)|[\_mbsnbcpy\_s, \_mbsnbcpy\_s\_l](../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)|Copiar `n` bytes de una cadena a una cadena de destino.|  
|[\_mbsnbset, \_mbsnbset\_l](../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)|[\_mbsnbset\_s, \_mbsnbset\_s\_l](../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md)|Configurar los primeros `n` bytes de una cadena en un carácter especificado|  
|[mbsrtowcs](../c-runtime-library/reference/mbsrtowcs.md)|[mbsrtowcs\_s](../c-runtime-library/reference/mbsrtowcs-s.md)|Convertir una cadena de caracteres multibyte en una cadena correspondiente de caracteres anchos|  
|[mbstowcs, \_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)|[mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convertir una secuencia de caracteres multibyte en una secuencia correspondiente de caracteres anchos|  
|[memcpy, wmemcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)|[memcpy\_s, wmemcpy\_s](../c-runtime-library/reference/memcpy-s-wmemcpy-s.md)|Copiar caracteres entre búferes|  
|[memmove, wmemmove](../c-runtime-library/reference/memmove-wmemmove.md)|[memmove\_s, wmemmove\_s](../c-runtime-library/reference/memmove-s-wmemmove-s.md)|Mover un búfer a otro|  
|[\_mktemp, \_wmktemp](../c-runtime-library/reference/mktemp-wmktemp.md)|[\_mktemp\_s, \_wmktemp\_s](../c-runtime-library/reference/mktemp-s-wmktemp-s.md)|Crear un nombre de archivo único|  
|[printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)|Imprimir el resultado con formato en el flujo de salida estándar|  
|[\_putenv, \_wputenv](../c-runtime-library/reference/putenv-wputenv.md)|[\_putenv\_s, \_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|Crear, modificar o quitar variables de entorno|  
|[qsort](../c-runtime-library/reference/qsort.md)|[qsort\_s](../c-runtime-library/reference/qsort-s.md)|Realizar una ordenación rápida|  
|[rand](../c-runtime-library/reference/rand.md)|[rand\_s](../c-runtime-library/reference/rand-s.md)|Generar un número pseudoaleatorio|  
|[scanf, \_scanf\_l, wscanf, \_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)|[scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)|Leer datos con formato del flujo de entrada estándar|  
|[\_searchenv, \_wsearchenv](../c-runtime-library/reference/searchenv-wsearchenv.md)|[\_searchenv\_s, \_wsearchenv\_s](../c-runtime-library/reference/searchenv-s-wsearchenv-s.md)|Buscar un archivo mediante rutas de acceso de entorno|  
|[snprintf, \_snprintf, \_snprintf\_l, \_snwprintf, \_snwprintf\_l](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)|[\_snprintf\_s, \_snprintf\_s\_l, \_snwprintf\_s, \_snwprintf\_s\_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)|Escribe datos con formato en una cadena|  
|[\_snscanf, \_snscanf\_l, \_snwscanf, \_snwscanf\_l](../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md)|[\_snscanf\_s, \_snscanf\_s\_l, \_snwscanf\_s, \_snwscanf\_s\_l](../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md)|Leer datos con formato de una longitud especificada de una cadena|  
|[\_sopen, \_wsopen](../c-runtime-library/reference/sopen-wsopen.md)|[\_sopen\_s, \_wsopen\_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Abrir un archivo para uso compartido|  
|[\_splitpath, \_wsplitpath](../c-runtime-library/reference/splitpath-wsplitpath.md)|[\_splitpath\_s, \_wsplitpath\_s](../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)|Dividir un nombre de ruta de acceso en componentes|  
|[sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[sprintf\_s, \_sprintf\_s\_l, swprintf\_s, \_swprintf\_s\_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)|Escribe datos con formato en una cadena|  
|[sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)|[sscanf\_s, \_sscanf\_s\_l, swscanf\_s, \_swscanf\_s\_l](../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)|Leer datos con formato de una cadena|  
|[strcat, wcscat, \_mbscat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)|[strcat\_s, wcscat\_s, \_mbscat\_s](../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md)|Anexar una cadena|  
|[strcpy, wcscpy, \_mbscpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|[strcpy\_s, wcscpy\_s, \_mbscpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)|Copiar una cadena|  
|[\_strdate, \_wstrdate](../c-runtime-library/reference/strdate-wstrdate.md)|[\_strdate\_s, \_wstrdate\_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|Devolver la fecha actual del sistema como cadena|  
|[strerror, \_strerror, \_wcserror, \_\_wcserror](../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md)|[strerror\_s, \_strerror\_s, \_wcserror\_s, \_\_wcserror\_s](../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md)|Obtiene un mensaje de error del sistema \(`strerror`, `_wcserror`\) o imprime un mensaje de error proporcionado por el usuario \(`_strerror`, `__wcserror`\)|  
|[\_strlwr, \_wcslwr, \_mbslwr, \_strlwr\_l, \_wcslwr\_l, \_mbslwr\_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md)|[\_strlwr\_s, \_strlwr\_s\_l, \_mbslwr\_s, \_mbslwr\_s\_l, \_wcslwr\_s, \_wcslwr\_s\_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Convertir una cadena a minúsculas|  
|[strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|[strncat\_s, \_strncat\_s\_l, wcsncat\_s, \_wcsncat\_s\_l, \_mbsncat\_s, \_mbsncat\_s\_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)|Anexar caracteres a una cadena|  
|[strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)|[strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)|Copia los caracteres de una cadena en otra|  
|[\_strnset, \_strnset\_l, \_wcsnset, \_wcsnset\_l, \_mbsnset, \_mbsnset\_l](../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)|[\_strnset\_s, \_strnset\_s\_l, \_wcsnset\_s, \_wcsnset\_s\_l, \_mbsnset\_s, \_mbsnset\_s\_l](../c-runtime-library/reference/strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md)|Establecer los primeros n caracteres de una cadena en el carácter especificado|  
|[\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[\_strset\_s, \_strset\_s\_l, \_wcsset\_s, \_wcsset\_s\_l, \_mbsset\_s, \_mbsset\_s\_l](../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md)|Establecer todos los caracteres de una cadena en el carácter especificado|  
|[\_strtime, \_wstrtime](../c-runtime-library/reference/strtime-wstrtime.md)|[\_strtime\_s, \_wstrtime\_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|Devolver la hora actual del sistema como cadena|  
|[strtok, \_strtok\_l, wcstok, \_wcstok\_l, \_mbstok, \_mbstok\_l](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)|[strtok\_s, \_strtok\_s\_l, wcstok\_s, \_wcstok\_s\_l, \_mbstok\_s, \_mbstok\_s\_l](../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)|Buscar el siguiente token en una cadena, con la configuración regional actual o con la configuración regional que se pase|  
|[\_strupr, \_strupr\_l, \_mbsupr, \_mbsupr\_l, \_wcsupr\_l, \_wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)|[\_strupr\_s, \_strupr\_s\_l, \_mbsupr\_s, \_mbsupr\_s\_l, \_wcsupr\_s, \_wcsupr\_s\_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Convertir una cadena a mayúsculas|  
|[tmpfile](../c-runtime-library/reference/tmpfile.md)|[tmpfile\_s](../c-runtime-library/reference/tmpfile-s.md)|Crear un archivo temporal|  
|[\_tempnam, \_wtempnam, tmpnam, \_wtmpnam](../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)|[tmpnam\_s, \_wtmpnam\_s](../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)|Generar nombres que puede usarse para crear archivos temporales|  
|[\_ultoa, \_ultow](../c-runtime-library/reference/ultoa-ultow.md)|[\_ultoa\_s, \_ultow\_s](../c-runtime-library/reference/ultoa-s-ultow-s.md)|Convertir un entero largo sin signo en cadena|  
|[\_umask](../c-runtime-library/reference/umask.md)|[\_umask\_s](../c-runtime-library/reference/umask-s.md)|Establecer la máscara de permisos de archivo predeterminados|  
|[\_vcprintf, \_vcprintf\_l, \_vcwprintf, \_vcwprintf\_l](../c-runtime-library/reference/vcprintf-vcprintf-l-vcwprintf-vcwprintf-l.md)|[\_vcprintf\_s, \_vcprintf\_s\_l, \_vcwprintf\_s, \_vcwprintf\_s\_l](../c-runtime-library/reference/vcprintf-s-vcprintf-s-l-vcwprintf-s-vcwprintf-s-l.md)|Escribir la salida con formato en la consola mediante un puntero a una lista de argumentos|  
|[vfprintf, \_vfprintf\_l, vfwprintf, \_vfwprintf\_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[vfprintf\_s, \_vfprintf\_s\_l, vfwprintf\_s, \_vfwprintf\_s\_l](../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)|Escribe un resultado con formato mediante un puntero a una lista de argumentos|  
|[vfscanf, vfwscanf](../c-runtime-library/reference/vfscanf-vfwscanf.md)|[vfscanf\_s, vfwscanf\_s](../c-runtime-library/reference/vfscanf-s-vfwscanf-s.md)|Leer datos con formato de un flujo|  
|[vprintf, \_vprintf\_l, vwprintf, \_vwprintf\_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[vprintf\_s, \_vprintf\_s\_l, vwprintf\_s, \_vwprintf\_s\_l](../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)|Escribe un resultado con formato mediante un puntero a una lista de argumentos|  
|[vscanf, vwscanf](../c-runtime-library/reference/vscanf-vwscanf.md)|[vscanf\_s, vwscanf\_s](../c-runtime-library/reference/vscanf-s-vwscanf-s.md)|Leer datos con formato del flujo de entrada estándar|  
|[vsnprintf, \_vsnprintf, \_vsnprintf\_l, \_vsnwprintf, \_vsnwprintf\_l](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)|[vsnprintf\_s, \_vsnprintf\_s, \_vsnprintf\_s\_l, \_vsnwprintf\_s, \_vsnwprintf\_s\_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)|Escribe un resultado con formato mediante un puntero a una lista de argumentos|  
|[vsprintf, \_vsprintf\_l, vswprintf, \_vswprintf\_l, \_\_vswprintf\_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[vsprintf\_s, \_vsprintf\_s\_l, vswprintf\_s, \_vswprintf\_s\_l](../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)|Escribe un resultado con formato mediante un puntero a una lista de argumentos|  
|[vsscanf, vswscanf](../c-runtime-library/reference/vsscanf-vswscanf.md)|[vsscanf\_s, vswscanf\_s](../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)|Leer datos con formato de una cadena|  
|[wcrtomb](../c-runtime-library/reference/wcrtomb.md)|[wcrtomb\_s](../c-runtime-library/reference/wcrtomb-s.md)|Convertir un carácter ancho en su representación de carácter multibyte|  
|[wcsrtombs](../c-runtime-library/reference/wcsrtombs.md)|[wcsrtombs\_s](../c-runtime-library/reference/wcsrtombs-s.md)|Convertir una cadena de caracteres anchos en su representación de cadena de caracteres multibyte|  
|[wcstombs, \_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md)|[wcstombs\_s, \_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convertir una secuencia de caracteres anchos en una secuencia correspondiente de caracteres multibyte|  
|[wctomb, \_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md)|[wctomb\_s, \_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convertir un carácter ancho en el carácter multibyte correspondiente|  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)