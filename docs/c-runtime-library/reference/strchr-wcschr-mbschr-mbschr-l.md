---
title: "strchr, wcschr, _mbschr, _mbschr_l | Microsoft Docs"
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
  - "strchr"
  - "wcschr"
  - "_mbschr_l"
  - "_mbschr"
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
  - "_ftcschr"
  - "strchr"
  - "wcschr"
  - "_tcschr"
  - "_mbschr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcschr (función)"
  - "_mbschr (función)"
  - "_mbschr_l (función)"
  - "_tcschr (función)"
  - "caracteres [C++], buscar en cadenas"
  - "ftcschr (función)"
  - "mbschr (función)"
  - "mbschr_l (función)"
  - "strchr (función)"
  - "cadenas [C++], buscar"
  - "tcschr (función)"
  - "wcschr (función)"
ms.assetid: 2639905d-e983-43b7-b885-abef32cfac43
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strchr, wcschr, _mbschr, _mbschr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Busca un carácter en una cadena con la configuración regional actual o una categoría especificada de conversión de estado LC\_CTYPE.  
  
> [!IMPORTANT]
>  `_mbschr` y `_mbschr_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *strchr(  
   const char *str,  
   int c   
);  // C only  
char *strchr(  
   char * str,  
   int c   
); // C++ only  
const char *strchr(  
   const char * str,  
   int c   
); // C++ only  
wchar_t *wcschr(  
   const wchar_t *str,  
   wchar_t c   
); // C only  
wchar_t *wcschr(  
   wchar_t *str,  
   wchar_t c   
);  // C++ only  
const wchar_t *wcschr(  
   const wchar_t *str,  
   wchar_t c   
);  // C++ only  
unsigned char *_mbschr(  
   const unsigned char *str,  
   unsigned int c   
); // C only  
unsigned char *_mbschr(  
   unsigned char *str,  
   unsigned int c   
); // C++ only  
const unsigned char *_mbschr(  
   const unsigned char *str,  
   unsigned int c   
); // C++ only  
unsigned char *_mbschr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C only   
unsigned char *_mbschr_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbschr_l(  
   const unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena de origen terminada en NULL.  
  
 `c`  
 Carácter que se va a buscar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a la primera aparición de `c` en `str`, o `NULL` si `c` no se encuentra.  
  
## Comentarios  
 La función `strchr` encuentra la primera aparición de `c` en `str`, o devuelve `NULL` si `c` no se encuentra.  En la búsqueda se incluye el carácter nulo de terminación.  
  
 `wcschr`, `_mbschr` y `_mbschr_l` son versiones de caracteres anchos y multibyte de `strchr`.  Los argumentos y el valor devuelto de `wcschr` son cadenas de caracteres anchos; los de `_mbschr` son cadenas de caracteres multibyte.  `_mbschr` reconoce secuencias de caracteres multibyte.  Además, si la cadena es un puntero nulo, `_mbschr` invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbschr` devuelve `NULL` y establece `errno` en `EINVAL`.  `strchr` y `wcschr` no validan sus parámetros.  Estas tres funciones se comportan exactamente igual.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional. Para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C, estas funciones toman un puntero `const` como primer argumento.  En C\+\+, hay disponibles dos sobrecargas.  La sobrecarga que toma un puntero a `const` devuelve un puntero a `const`; la versión que contiene un puntero a un valor que no es `const` devuelve un puntero a un valor que no es `const`.  La macro \_CONST\_CORRECT\_OVERLOADS se define si están disponibles tanto las versiones `const` como no `const` de estas funciones.  Si necesita un comportamiento que no sea `const` para ambas sobrecargas de C\+\+, defina el símbolo \_CONST\_RETURN.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcschr`|`strchr`|`_mbschr`|`wcschr`|  
|**\_n\/a**|**no disponible**|`_mbschr_l`|**no disponible**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strchr`|\<string.h\>|  
|`wcschr`|\<string.h\> o \<wchar.h\>|  
|`_mbschr`, `_mbschr_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strchr.c  
//   
// This program illustrates searching for a character  
// with strchr (search forward) or strrchr (search backward).  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int  ch = 'r';  
  
char string[] = "The quick brown dog jumps over the lazy fox";  
char fmt1[] =   "         1         2         3         4         5";  
char fmt2[] =   "12345678901234567890123456789012345678901234567890";  
  
int main( void )  
{  
   char *pdest;  
   int result;  
  
   printf_s( "String to be searched:\n      %s\n", string );  
   printf_s( "      %s\n      %s\n\n", fmt1, fmt2 );  
   printf_s( "Search char:   %c\n", ch );  
  
   // Search forward.   
   pdest = strchr( string, ch );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf_s( "Result:   first %c found at position %d\n",   
              ch, result );  
   else  
      printf_s( "Result:   %c not found\n", ch );  
  
   // Search backward.   
   pdest = strrchr( string, ch );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf_s( "Result:   last %c found at position %d\n", ch, result );  
   else  
      printf_s( "Result:\t%c not found\n", ch );  
}  
```  
  
  **Cadena que se va a buscar:**  
 **The quick brown dog jumps over the lazy fox**  
 **1         2         3         4         5**  
 **12345678901234567890123456789012345678901234567890**  
**Search char:   r**  
**Result:   first r found at position 12**  
**Result:   last r found at position 30**   
## Equivalente en .NET Framework  
 [System::String::IndexOf](https://msdn.microsoft.com/en-us/library/system.string.indexof.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn, wcscspn, \_mbscspn, \_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strpbrk, wcspbrk, \_mbspbrk, \_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strstr, wcsstr, \_mbsstr, \_mbsstr\_l](../../c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l.md)