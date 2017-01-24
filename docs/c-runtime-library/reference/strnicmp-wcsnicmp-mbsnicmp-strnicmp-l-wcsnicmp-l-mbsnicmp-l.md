---
title: "_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l | Microsoft Docs"
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
  - "_wcsnicmp"
  - "_strnicmp_l"
  - "_wcsnicmp_l"
  - "_strnicmp"
  - "_mbsnicmp"
  - "_mbsnicmp_l"
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
  - "wcsnicmp_l"
  - "_strnicmp"
  - "_ftcsnicmp"
  - "mbsnicmp_l"
  - "_ftcsncicmp"
  - "mbsnicmp"
  - "_tcsncicmp"
  - "_mbsnicmp"
  - "_tcsnicmp"
  - "strnicmp_l"
  - "_wcsnicmp"
  - "_wcsnicmp_l"
  - "CORECRT_WSTRING/_wcsnicmp"
  - "CORECRT_WSTRING/_wcsnicmp_l"
  - "string/_strnicmp"
  - "string/_strnicmp_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsncicmp (función)"
  - "_ftcsnicmp (función)"
  - "_mbsnicmp (función)"
  - "_mbsnicmp_l (función)"
  - "_strnicmp (función)"
  - "_strnicmp_l (función)"
  - "_tcsncicmp (función)"
  - "_tcsnicmp (función)"
  - "_wcsnicmp (función)"
  - "_wcsnicmp_l (función)"
  - "caracteres [C++], comparar"
  - "ftcsncicmp (función)"
  - "ftcsnicmp (función)"
  - "mbsnicmp (función)"
  - "mbsnicmp_l (función)"
  - "comparación de cadenas [C++], minúsculas"
  - "comparación de cadenas [C++], strncmp (función)"
  - "cadenas [C++], comparar caracteres de"
  - "strncmp (función)"
  - "strnicmp_l (función)"
  - "tcsncicmp (función)"
  - "tcsnicmp (función)"
  - "wcsnicmp (función)"
  - "wcsnicmp_l (función)"
ms.assetid: df6e5037-4039-4c85-a0a6-21d4ef513966
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara el número de caracteres especificado de dos cadenas sin distinción entre mayúsculas y minúsculas.  
  
> [!IMPORTANT]
>  `_mbsnicmp` y `_mbsnicmp_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _strnicmp(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int _wcsnicmp(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsnicmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _strnicmp_l(  
   const char *string1,  
   const char *string2,  
   size_t count,  
   _locale_t locale  
);  
int _wcsnicmp_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count,  
   _locale_t locale  
);  
int _mbsnicmp_l(  
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
 Indica la relación entre las subcadenas, como se muestra a continuación.  
  
|Valor devuelto|Descripción|  
|--------------------|-----------------|  
|\< 0|La subcadena `string1` es menor que la subcadena `string2`.|  
|0|La subcadena `string1` es idéntica a la subcadena `string2`.|  
|\> 0|La subcadena `string1` es mayor que la subcadena `string2`.|  
  
 Si se produce un error de validación de parámetros, estas funciones devuelven `_NLSCMPERROR`, que se define en \<string.h\> y \<mbstring.h\>.  
  
## Comentarios  
 La función `_strnicmp` compara ordinalmente, a lo sumo, los primeros `count` caracteres de `string1` y `string2`.  La comparación se realiza sin distinguir entre mayúsculas y minúsculas, ya que todos los caracteres se convierten a minúsculas.  `_strnicmp` es una versión sin distinción entre mayúsculas y minúsculas de `strncmp`.  La comparación finaliza si se llega a un carácter nulo de terminación en una de las cadenas antes de que se comparen `count` caracteres.  Si las cadenas son iguales cuando se llega a un carácter nulo de terminación en una de las cadenas antes de que se comparen `count` caracteres, la cadena más corta es menor.  
  
 Los caracteres 91 a 96 en la tabla ASCII \("\[", "\\", "\]", "^", "\_" y "\`"\) se consideran menores que cualquier carácter alfabético.  Esta ordenación es idéntica a la de `stricmp`.  
  
 `_wcsnicmp` y `_mbsnicmp` son versiones de caracteres anchos y multibyte de `_strnicmp`.  Los argumentos de `_wcsnicmp` son cadenas de caracteres anchos; los de `_mbsnicmp` son cadenas de caracteres multibyte.  `_mbsnicmp` reconoce secuencias de caracteres multibyte según la página actual de códigos multibyte y devuelve `_NLSCMPERROR` cuando se produce un error.  Para obtener más información, vea [Páginas de códigos](../../c-runtime-library/code-pages.md).  Estas tres funciones se comportan exactamente igual.  Estas funciones se ven afectadas por la configuración regional. Las versiones que no tienen el sufijo `_l` usan la configuración regional local para el comportamiento que depende de la configuración regional; las versiones que sí tienen el sufijo `_l` utilizan la `locale` pasada.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Todas estas funciones validan sus parámetros.  Si `string1` o `string2` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `_NLSCMPERROR` y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsncicmp`|`_strnicmp`|`_mbsnicmp`|`_wcsnicmp`|  
|`_tcsnicmp`|`_strnicmp`|`_mbsnbicmp`|`_wcsnicmp`|  
|`_tcsncicmp_l`|`_strnicmp_l`|`_mbsnicmp_l`|`_wcsnicmp_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strnicmp`, `_strnicmp_l`|\<string.h\>|  
|`_wcsnicmp`, `_wcsnicmp_l`|\<string.h\> o \<wchar.h\>|  
|`_mbsnicmp`, `_mbsnicmp_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [strncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md).  
  
## Equivalente en .NET Framework  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)