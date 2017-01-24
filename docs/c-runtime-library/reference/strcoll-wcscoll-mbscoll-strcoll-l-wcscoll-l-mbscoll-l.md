---
title: "strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l | Microsoft Docs"
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
  - "wcscoll"
  - "_mbscoll"
  - "_mbscoll_l"
  - "strcoll"
  - "_strcoll_l"
  - "_wcscoll_l"
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
  - "wcscoll"
  - "_mbscoll"
  - "_tcscoll"
  - "_ftcscoll"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "páginas de códigos, usar para comparaciones de cadenas"
  - "mbscoll (función)"
  - "wcscoll_l (función)"
  - "ftcscoll (función)"
  - "wcscoll (función)"
  - "_strcoll_l (función)"
  - "tcscoll (función)"
  - "_ftcscoll (función)"
  - "_tcscoll (función)"
  - "_wcscoll_l (función)"
  - "_mbscoll (función)"
  - "strcoll_l (función)"
  - "strcoll (función)"
  - "cadenas [C++], comparar por página de códigos"
ms.assetid: 900a7540-c7ec-4c2f-b292-7a85f63e3fe8
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara cadenas usando la configuración regional actual o una categoría de conversión de estado LC\_COLLATE especificada.  
  
> [!IMPORTANT]
>  `_mbscoll` y `_mbscoll_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int strcoll(  
   const char *string1,  
   const char *string2   
);  
int wcscoll(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscoll(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _strcoll_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale   
);  
int wcscoll_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale   
);  
int _mbscoll_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale   
);  
```  
  
#### Parámetros  
 `string1`, `string2`  
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
  
 Cada una de estas funciones devuelve `_NLSCMPERROR` si se produce un error.  Para usar `_NLSCMPERROR`, incluya STRING.H o MBSTRING.H.  `wcscoll` puede producir un error si `string1` o `string2` es un valor nulo o contiene códigos de caracteres anchos fuera del dominio de la secuencia de intercalación.  Cuando se produce un error, `wcscoll` puede establecer `errno` en `EINVAL`.  Para comprobar si hay un error en una llamada a `wcscoll`, establezca `errno` en 0 y observe `errno` después de llamar a `wcscoll`.  
  
## Comentarios  
 Cada una de estas funciones compara, con distinción entre mayúsculas y minúsculas, `string1` con `string2`, de acuerdo con la página de códigos actualmente en uso.  Estas funciones solo se deben usar cuando el orden del juego de caracteres y el orden de los caracteres lexicográficos son distintos en la página de códigos actual, y la diferencia influye en la comparación de cadenas.  
  
 Todas estas funciones validan sus parámetros.  Si `string1` o `string2` es un puntero nulo, o si `count` es mayor que `INT_MAX`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `_NLSCMPERROR` y establecen `errno` en `EINVAL`.  
  
 La comparación de las dos cadenas es una operación dependiente de la configuración regional, ya que cada configuración regional tiene distintas reglas para ordenar los caracteres.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional del subproceso actual para este comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas a la función correspondiente sin el sufijo, salvo que usan la configuración regional que se pasa como parámetro en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcscoll`|`strcoll`|`_mbscoll`|`wcscoll`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strcoll`|\<string.h\>|  
|`wcscoll`|\<wchar.h\>, \<string.h\>|  
|`_mbscoll`, `_mbscoll_l`|\<mbstring.h\>|  
|`_strcoll_l`|\<string.h\>|  
|`_wcscoll_l`|\<wchar.h\>, \<string.h\>|  
  
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