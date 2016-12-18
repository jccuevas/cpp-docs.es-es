---
title: "_mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbicoll_l"
  - "_mbsnbcoll_l"
  - "_mbsnbcoll"
  - "_mbsnbicoll"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbsnbicoll"
  - "mbsnbcoll"
  - "mbsnbicoll_l"
  - "_mbsnbcoll"
  - "_mbsnbicoll"
  - "_ftcsnicoll"
  - "_ftcsncoll"
  - "mbsnbcoll_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcoll (función)"
  - "_mbsnbcoll_l (función)"
  - "_mbsnbicoll (función)"
  - "_mbsnbicoll_l (función)"
  - "_tcsncoll (función)"
  - "_tcsnicoll (función)"
  - "mbsnbcoll (función)"
  - "mbsnbcoll_l (función)"
  - "mbsnbicoll (función)"
  - "mbsnbicoll_l (función)"
  - "tcsncoll (función)"
  - "tcsnicoll (función)"
ms.assetid: d139ed63-ccba-4458-baa2-61cbcef03e94
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbcoll, _mbsnbcoll_l, _mbsnbicoll, _mbsnbicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara `n` bytes de dos cadenas de caracteres multibyte usando la información de la página de códigos multibyte.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _mbsnbcoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbcoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnbicoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `string1, string2`  
 Cadenas que se van a comparar.  
  
 `count`  
 Número de bytes que se van a comparar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 El valor devuelto indica la relación de las subcadenas de `string1` y `string2`.  
  
|Valor devuelto|Descripción|  
|--------------------|-----------------|  
|\< 0|La subcadena `string1` es menor que la subcadena `string2`.|  
|0|La subcadena `string1` es idéntica a la subcadena `string2`.|  
|\> 0|La subcadena `string1` es mayor que la subcadena `string2`.|  
  
 Si `string1` o `string2` es `NULL`, o si `count` es mayor que `INT_MAX`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `_NLSCMPERROR` y establecen `errno` en `EINVAL`.  Para usar `_NLSCMPERROR`, incluya String.h o Mbstring.h.  
  
## Comentarios  
 Cada una de estas funciones intercala, como máximo, los primeros `count` bytes de `string1` y `string2`, y devuelve un valor que indica la relación entre las subcadenas resultantes de `string1` y `string2`.  Si el byte final de la subcadena de `string1` o `string2` es un byte inicial, no se incluye en la comparación; estas funciones solo comparan caracteres completos de las subcadenas.  `_mbsnbicoll` es una versión sin distinción entre mayúsculas y minúsculas de `_mbsnbcoll`.  Al igual que `_mbsnbcmp` y `_mbsnbicmp`, `_mbsnbcoll` y `_mbsnbicoll` intercalan las dos cadenas de caracteres multibyte según el orden lexicográfico especificado por la [página de códigos](../../c-runtime-library/code-pages.md) multibyte que se esté usando.  
  
 En el caso de algunas páginas de códigos y los juegos de caracteres correspondientes, el orden de los caracteres del juego de caracteres no es igual que el orden lexicográfico de los caracteres.  En la configuración regional de "C" no es así: el orden de los caracteres del juego de caracteres ASCII es igual que el orden lexicográfico de los caracteres.  Sin embargo, en algunas páginas de códigos europeas, por ejemplo, el carácter “a” \(valor 0x61\) precede el carácter “ä” \(valor 0xE4\) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente.  Para realizar una comparación lexicográfica de cadenas por bytes en un caso así, use `_mbsnbcoll` en lugar de `_mbsnbcmp`; para comprobar solo si las cadenas son iguales, use `_mbsnbcmp`.  
  
 Dado que las funciones `coll` intercalan lexicográficamente las cadenas para compararlas mientras que las funciones `cmp` prueban simplemente si las cadenas, las funciones `coll` son mucho más lentas que las versiones correspondientes de `cmp`.  En consecuencia, las funciones `coll` solo se deben usar cuando el orden del juego de caracteres y el orden de los caracteres lexicográficos son distintos en la página de códigos actual, y la diferencia influye en la comparación.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsncoll`|[\_strncoll](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll`|[\_wcsncoll](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsncoll_l`|[\_strncoll, \_wcsncoll, \_mbsncoll, \_strncoll\_l, \_wcsncoll\_l, \_mbsncoll\_l](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|`_mbsnbcoll_l`|[\_wcsncoll\_l](../../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|  
|`_tcsnicoll`|[\_strnicoll](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll`|[\_wcsnicoll](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
|`_tcsnicoll_l`|[\_strnicoll\_l](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|`_mbsnbicoll_l`|[\_wcsnicoll\_l](../../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnbcoll`|\<mbstring.h\>|  
|`_mbsnbcoll_l`|\<mbstring.h\>|  
|`_mbsnbicoll`|\<mbstring.h\>|  
|`_mbsnbicoll_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat, \_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_mbsnbcmp, \_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_mbsnbicmp, \_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)