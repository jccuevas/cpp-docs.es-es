---
title: "strrchr, wcsrchr, _mbsrchr, _mbsrchr_l | Microsoft Docs"
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
  - "strrchr"
  - "wcsrchr"
  - "_mbsrchr"
  - "_mbsrchr_l"
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
  - "_tcsrchr"
  - "_ftcsrchr"
  - "strrchr"
  - "wcsrchr"
  - "_mbsrchr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsrchr (función)"
  - "_mbsrchr (función)"
  - "_mbsrchr_l (función)"
  - "_tcsrchr (función)"
  - "caracteres [C++], buscar"
  - "ftcsrchr (función)"
  - "mbsrchr (función)"
  - "mbsrchr_l (función)"
  - "examinar cadenas"
  - "cadenas [C++], examinar"
  - "strrchr (función)"
  - "tcsrchr (función)"
  - "wcsrchr (función)"
ms.assetid: 75cf2664-758e-49bb-bf6b-8a139cd474d2
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strrchr, wcsrchr, _mbsrchr, _mbsrchr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Examina una cadena para buscar la última repetición de un carácter.  
  
> [!IMPORTANT]
>  `_mbsrchr` y `_mbsrchr_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *strrchr(  
   const char *str,  
   int c   
); // C only  
char *strrchr(  
   char *str,  
   int c   
); // C++ only  
const char *strrchr(  
   const char *str,  
   int c   
); // C++ only  
wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C only  
wchar_t *wcsrchr(  
   wchar_t *str,  
   wchar_t c   
); // C++ only  
const wchar_t *wcsrchr(  
   const wchar_t *str,  
   wchar_t c   
); // C++ only  
unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C only  
unsigned char *_mbsrchr(  
   unsigned char *str,  
   unsigned int c   
); // C++ only  
const unsigned char *_mbsrchr(  
   const unsigned char *str,  
   unsigned int c   
); // C++ only  
unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C only  
unsigned char *_mbsrchr_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsrchr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL que se va a buscar.  
  
 `c`  
 Carácter que se va a buscar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero a la última repetición de `c` en `str`, o `NULL`  si no se encuentra `c`.  
  
## Comentarios  
 La función `strrchr` encuentra la última repetición de `c` \(convertida en `char`\) en `str`.  La búsqueda incluye el carácter nulo de terminación.  
  
 `wcsrchr` y `_mbsrchr` son versiones de caracteres anchos y multibyte de `strrchr`.  Los argumentos y el valor devuelto de `wcsrchr`  son cadenas de caracteres anchos; los de `_mbsrchr` son cadenas de caracteres multibyte.  
  
 En C, estas funciones toman un puntero `const` como primer argumento.  En C\+\+, hay disponibles dos sobrecargas.  La sobrecarga que toma un puntero a `const` devuelve un puntero a `const`; la versión que contiene un puntero a un valor que no es `const` devuelve un puntero a un valor que no es `const`.  La macro \_CONST\_CORRECT\_OVERLOADS se define si están disponibles tanto las versiones `const` como no `const` de estas funciones.  Si necesita un comportamiento que no sea `const` para ambas sobrecargas de C\+\+, defina el símbolo \_CONST\_RETURN.  
  
 `_mbsrchr` valida sus parámetros.  Si `str` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno`  se establece en `EINVAL`  y `_mbsrchr`  devuelve 0.  `strrchr` y `wcsrchr` no validan sus parámetros.  Estas tres funciones se comportan exactamente igual.  
  
 El valor de la categoría `LC_CTYPE`  de la configuración regional afecta al valor de salida; para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsrchr`|`strrchr`|`_mbsrchr`|`wcsrchr`|  
|**no disponible**|**no disponible**|`_mbsrchr_l`|**no disponible**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strrchr`|\<string.h\>|  
|`wcsrchr`|\<string.h\> o \<wchar.h\>|  
|`_mbsrchr`, `_mbsrchr_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Para obtener un ejemplo de la forma de usar `strrchr`, vea [strchr](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md).  
  
## Equivalente en .NET Framework  
 [System::String::LastIndexOf](https://msdn.microsoft.com/en-us/library/system.string.lastindexof.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strchr, wcschr, \_mbschr, \_mbschr\_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strcspn, wcscspn, \_mbscspn, \_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strpbrk, wcspbrk, \_mbspbrk, \_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)