---
title: "_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l | Microsoft Docs"
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
  - "_mbsicoll_l"
  - "_stricoll_l"
  - "_mbsicoll"
  - "_wcsicoll_l"
  - "_wcsicoll"
  - "_stricoll"
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
  - "stricoll"
  - "_stricoll"
  - "_wcsicoll"
  - "mbsicoll_l"
  - "_mbsicoll"
  - "_ftcsicoll"
  - "wcsicoll_l"
  - "_tcsicoll"
  - "mbsicoll"
  - "stricoll_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsicoll (función)"
  - "_mbsicoll (función)"
  - "_mbsicoll_l (función)"
  - "_stricoll (función)"
  - "_stricoll_l (función)"
  - "_tcsicoll (función)"
  - "_wcsicoll (función)"
  - "páginas de códigos, usar para comparaciones de cadenas"
  - "ftcsicoll (función)"
  - "mbsicoll (función)"
  - "mbsicoll_l (función)"
  - "stricoll (función)"
  - "stricoll_l (función)"
  - "comparación de cadenas [C++], específicas de referencias culturales"
  - "cadenas [C++], comparar por página de códigos"
  - "tcsicoll (función)"
ms.assetid: 8ec93016-5a49-49d2-930f-721566661d82
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara cadenas usando información específica de la configuración regional.  
  
> [!IMPORTANT]
>  `_mbsicoll` y `_mbsicoll_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _stricoll(  
   const char *string1,  
   const char *string2   
);  
int _wcsicoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `string1, string2`  
 Cadenas terminadas en NULL que se van a comparar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un valor que indica la relación entre `string1` y `string2`*,* como se indica a continuación.  
  
|Valor devuelto|Relación de string1 y string2|  
|--------------------|-----------------------------------|  
|\< 0|`string1` es menor que `string2`|  
|0|`string1` es idéntica a `string2`|  
|\> 0|`string1` es mayor que `string2`|  
|`_NLSCMPERROR`|Error.|  
  
 Cada una de estas funciones devuelve `_NLSCMPERROR`.  Para usar `_NLSCMPERROR`, incluya `STRING.H` o `MBSTRING.H`.  `_wcsicoll` puede producir un error si `string1` o `string2` contiene códigos de caracteres anchos fuera del dominio de la secuencia de intercalación.  Cuando se produce un error, `_wcsicoll` puede establecer `errno` en `EINVAL`.  Para comprobar si hay un error en una llamada a `_wcsicoll`, establezca `errno` en 0 y observe `errno` después de llamar a `_wcsicoll`.  
  
## Comentarios  
 Cada una de estas funciones compara, sin distinción entre mayúsculas y minúsculas, `string1` con `string2`, de acuerdo con la página de códigos actualmente en uso.  Estas funciones solo se deben usar cuando el orden del juego de caracteres y el orden de los caracteres lexicográficos son distintos en la página de códigos actual, y la diferencia influye en la comparación de cadenas.  
  
 `_stricmp` se diferencia de `_stricoll` en que la comparación `_stricmp` se ve afectada por `LC_CTYPE`, mientras que la comparación `_stricoll` se realiza en función de las categorías `LC_CTYPE` y `LC_COLLATE` de la configuración regional.  Para obtener más información sobre la categoría `LC_COLLATE`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) y [Categorías de configuración regional](../../c-runtime-library/locale-categories.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Todas estas funciones validan sus parámetros.  Si `string1` o `string2` es un puntero a `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `_NLSCMPERROR` y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsicoll`|`_stricoll`|`_mbsicoll`|`_wcsicoll`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_stricoll`, `_stricoll_l`|\<string.h\>|  
|`_wcsicoll`, `_wcsicoll_l`|\<wchar.h\>, \<string.h\>|  
|`_mbsicoll`, `_mbsicoll_l`|\<mbstring.h\>|  
  
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