---
title: "_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strncoll"
  - "_mbsncoll_l"
  - "_wcsncoll"
  - "_wcsncoll_l"
  - "_mbsncoll"
  - "_strncoll_l"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbsncoll_l"
  - "strncoll"
  - "_wcsncoll"
  - "_tcsnccoll"
  - "_ftcsnccoll"
  - "wcsncoll"
  - "_mbsncoll"
  - "wcsncoll_l"
  - "strncoll_l"
  - "_ftcsncoll"
  - "_strncoll"
  - "_tcsncoll"
  - "mbsncoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsnccoll (función)"
  - "_ftcsncoll (función)"
  - "_mbsncoll (función)"
  - "_mbsncoll_l (función)"
  - "_strncoll (función)"
  - "_strncoll_l (función)"
  - "_tcsnccoll (función)"
  - "_tcsncoll (función)"
  - "_wcsncoll (función)"
  - "_wcsncoll_l (función)"
  - "páginas de códigos, usar para comparaciones de cadenas"
  - "ftcsnccoll (función)"
  - "ftcsncoll (función)"
  - "mbsncoll (función)"
  - "mbsncoll_l (función)"
  - "cadenas [C++], comparar por página de códigos"
  - "strncoll (función)"
  - "strncoll_l (función)"
  - "tcsnccoll (función)"
  - "tcsncoll (función)"
  - "wcsncoll (función)"
  - "wcsncoll_l (función)"
ms.assetid: e659a5a4-8afe-4033-8e72-17ffd4bdd8e9
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara cadenas usando información específica de la configuración regional.  
  
> [!IMPORTANT]
>  `_mbsncoll` y `_mbsncoll_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _strncoll(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsncoll(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncoll(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strncoll_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsncoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsncoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `string1, string2`  
 Cadenas terminadas en NULL que se van a comparar.  
  
 `count`  
 Número de caracteres que se van a comparar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un valor que indica la relación de las subcadenas de `string1` y `string2`, como se indica a continuación.  
  
|Valor devuelto|Relación de string1 y string2|  
|--------------------|-----------------------------------|  
|\< 0|`string1` es menor que `string2`.|  
|0|`string1` es idéntica a `string2`.|  
|\> 0|`string1` es mayor que `string2`.|  
  
 Cada una de estas funciones devuelve `_NLSCMPERROR`.  Para usar `_NLSCMPERROR`, incluya STRING.h o MBSTRING.h.  `_wcsncoll` puede producir un error si `string1` o `string2` contiene códigos de caracteres anchos que están fuera del dominio de la secuencia de intercalación.  Cuando se produce un error, `_wcsncoll` puede establecer `errno` en `EINVAL`.  Para comprobar si hay un error en una llamada a `_wcsncoll`, establezca `errno` en 0 y observe `errno` después de llamar a `_wcsncoll`.  
  
## Comentarios  
 Cada una de estas funciones realiza una comparación con distinción entre mayúsculas y minúsculas de los primeros `count` caracteres de `string1` y `string2` según la página de códigos que esté en uso.  Use estas funciones solo cuando el orden del juego de caracteres y el orden de los caracteres lexicográficos sean distintos en la página de códigos y cuando la diferencia influya en la comparación de cadenas.  El orden del conjunto de caracteres depende de la configuración regional.  Las versiones de estas funciones que no tienen el sufijo `_l` usan la configuración regional actual, pero las versiones de estas funciones que tienen el sufijo `_l` usan la configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Todas estas funciones validan sus parámetros.  Si `string1` o `string2` es un puntero nulo, o si `count` es mayor que `INT_MAX`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `_NLSCMPERROR` y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnccoll`|`_strncoll`|`_mbsncoll`|`_wcsncoll`|  
|`_tcsncoll`|`_strncoll`|[\_mbsnbcoll](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)|`_wcsncoll`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strncoll`, `_strncoll_l`|\<string.h\>|  
|`_wcsncoll`, `_wcsncoll_l`|\<wchar.h\> o \<string.h\>|  
|`_mbsncoll`, `_mbsncoll_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_mbsnbcoll, \_mbsnbcoll\_l, \_mbsnbicoll, \_mbsnbicoll\_l](../../c-runtime-library/reference/mbsnbcoll-mbsnbcoll-l-mbsnbicoll-mbsnbicoll-l.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [\_stricmp, \_wcsicmp, \_mbsicmp, \_stricmp\_l, \_wcsicmp\_l, \_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strxfrm, wcsxfrm, \_strxfrm\_l, \_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)