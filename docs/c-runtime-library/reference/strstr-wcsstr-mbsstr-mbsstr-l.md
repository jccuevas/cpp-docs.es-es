---
title: "strstr, wcsstr, _mbsstr, _mbsstr_l | Microsoft Docs"
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
  - "_mbsstr"
  - "wcsstr"
  - "_mbsstr_l"
  - "strstr"
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
  - "_fstrstr"
  - "_ftcsstr"
  - "strstr"
  - "wcsstr"
  - "_mbsstr"
  - "_tcsstr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrstr (función)"
  - "_ftcsstr (función)"
  - "_mbsstr (función)"
  - "_mbsstr_l (función)"
  - "_tcsstr (función)"
  - "fstrstr (función)"
  - "ftcsstr (función)"
  - "mbsstr (función)"
  - "mbsstr_l (función)"
  - "cadenas [C++], buscar"
  - "strstr (función)"
  - "subcadenas, buscar"
  - "tcsstr (función)"
  - "wcsstr (función)"
ms.assetid: 03d70c3f-2473-45cb-a5f8-b35beeb2748a
caps.latest.revision: 32
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strstr, wcsstr, _mbsstr, _mbsstr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero a la primera aparición de una cadena de búsqueda en una cadena.  
  
> [!IMPORTANT]
>  `_mbsstr` y `_mbsstr_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *strstr(  
   const char *str,  
   const char *strSearch   
); // C only  
char *strstr(  
   char *str,  
   const char *strSearch   
); // C++ only  
const char *strstr(  
   const char *str,  
   const char *strSearch   
); // C++ only  
wchar_t *wcsstr(  
   const wchar_t *str,  
   const wchar_t *strSearch   
); // C only  
wchar_t *wcsstr(  
   wchar_t *str,  
   const wchar_t *strSearch   
); // C++ only  
const wchar_t *wcsstr(  
   const wchar_t *str,  
   const wchar_t *strSearch   
); // C++ only  
unsigned char *_mbsstr(  
   const unsigned char *str,  
   const unsigned char *strSearch   
); // C only  
unsigned char *_mbsstr(  
   unsigned char *str,  
   const unsigned char *strSearch   
); // C++ only  
const unsigned char *_mbsstr(  
   const unsigned char *str,  
   const unsigned char *strSearch   
); // C++ only  
unsigned char *_mbsstr_l(  
   const unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C only  
unsigned char *_mbsstr_l(  
   unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbsstr_l(  
   const unsigned char *str,  
   const unsigned char *strSearch,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL que se va a buscar.  
  
 `strSearch`  
 Cadena terminada en NULL que se va a buscar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero a la primera aparición de `strSearch` en `str`, o `NULL` si `strSearch` no aparece en `str`.  Si `strSearch` señala a una cadena de longitud cero, la función devuelve `str`.  
  
## Comentarios  
 La función `strstr` devuelve un puntero a la primera aparición de `strSearch` en `str`.  En la búsqueda no se incluyen los caracteres nulos de finalización.  `wcsstr` es la versión con caracteres anchos de `strstr` y `_mbsstr` es la versión de caracteres multibyte.  Los argumentos y el valor devuelto de `wcsstr` son cadenas de caracteres anchos; los de `_mbsstr` son cadenas de caracteres multibyte.  `_mbsstr` valida sus parámetros.  Si `str` o `strSearch` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbsstr` establece `errno` en `EINVAL` y devuelve 0.  `strstr` y `wcsstr` no validan sus parámetros.  Estas tres funciones se comportan exactamente igual.  
  
> [!IMPORTANT]
>  Estas funciones podrían provocar la amenaza de un problema de saturación del búfer.  Los problemas de saturación del búfer se pueden usar para atacar un sistema, porque pueden permitir la ejecución de código arbitrario, lo que podría dar lugar a un aumento de privilegios injustificado.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 En C, estas funciones toman un puntero `const` como primer argumento.  En C\+\+, hay disponibles dos sobrecargas.  La sobrecarga que toma un puntero a `const` devuelve un puntero a `const`; la versión que contiene un puntero a un valor que no es `const` devuelve un puntero a un valor que no es `const`.  La macro \_CONST\_CORRECT\_OVERLOADS se define si están disponibles tanto las versiones `const` como no `const` de estas funciones.  Si necesita un comportamiento que no sea `const` para ambas sobrecargas de C\+\+, defina el símbolo \_CONST\_RETURN.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones que tienen el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsstr`|`strstr`|`_mbsstr`|`wcsstr`|  
|**no disponible**|**no disponible**|`_mbsstr_l`|**no disponible**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strstr`|\<string.h\>|  
|`wcsstr`|\<string.h\> o \<wchar.h\>|  
|`_mbsstr`, `_mbsstr_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strstr.c  
  
#include <string.h>  
#include <stdio.h>  
  
char str[] =    "lazy";  
char string[] = "The quick brown dog jumps over the lazy fox";  
char fmt1[] =   "         1         2         3         4         5";  
char fmt2[] =   "12345678901234567890123456789012345678901234567890";  
  
int main( void )  
{  
   char *pdest;  
   int  result;  
   printf( "String to be searched:\n   %s\n", string );  
   printf( "   %s\n   %s\n\n", fmt1, fmt2 );  
   pdest = strstr( string, str );  
   result = (int)(pdest - string + 1);  
   if ( pdest != NULL )  
      printf( "%s found at position %d\n", str, result );  
   else  
      printf( "%s not found\n", str );  
}  
```  
  
  **Cadena que se va a buscar:**  
 **The quick brown dog jumps over the lazy fox**  
 **1         2         3         4         5**  
 **12345678901234567890123456789012345678901234567890**  
**lazy se encuentra en la posición 36**   
## Equivalente en .NET Framework  
 [System::String::IndexOf](https://msdn.microsoft.com/en-us/library/system.string.indexof.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn, wcscspn, \_mbscspn, \_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strpbrk, wcspbrk, \_mbspbrk, \_mbspbrk\_l](../../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [basic\_string::find](../Topic/basic_string::find.md)