---
title: "strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbspbrk"
  - "wcspbrk"
  - "_mbspbrk_l"
  - "strpbrk"
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
  - "_fstrpbrk"
  - "_mbspbrk"
  - "strpbrk"
  - "_tcspbrk"
  - "_ftcspbrk"
  - "wcspbrk"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fstrpbrk (función)"
  - "_ftcspbrk (función)"
  - "_mbspbrk (función)"
  - "_mbspbrk_l (función)"
  - "_tcspbrk (función)"
  - "juegos de caracteres [C++], buscar caracteres en cadenas"
  - "caracteres [C++], examinar cadenas"
  - "fstrpbrk (función)"
  - "ftcspbrk (función)"
  - "mbspbrk (función)"
  - "mbspbrk_l (función)"
  - "cadenas [C++], examinar"
  - "strpbrk (función)"
  - "tcspbrk (función)"
  - "wcspbrk (función)"
ms.assetid: 80b504f7-a167-4dde-97ad-4ae3000dc810
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Examina cadenas para buscar caracteres de juegos de caracteres especificados.  
  
> [!IMPORTANT]
>  `_mbspbrk` y `_mbspbrk_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C only  
char *strpbrk(  
   char *str,  
   const char *strCharSet   
); // C++ only  
const char *strpbrk(  
   const char *str,  
   const char *strCharSet   
); // C++ only  
wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C only  
wchar_t *wcspbrk(  
   wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
const wchar_t *wcspbrk(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
); // C++ only  
unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C only  
unsigned char *_mbspbrk(  
   unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
const unsigned char *_mbspbrk(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
); // C++ only  
unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C only  
unsigned char *_mbspbrk_l(  
   unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
); // C++ only  
const unsigned char *_mbspbrk_l(  
   const unsigned char *str,  
   const unsigned char* strCharSet,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL en la que se ha buscado.  
  
 `strCharSet`  
 Juego de caracteres terminado en NULL.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero a la primera aparición de cualquier carácter de `strCharSet` que esté en `str`, o un puntero `NULL` si los dos argumentos de cadena no tienen ningún carácter en común.  
  
## Comentarios  
 La función `strpbrk` devuelve un puntero a la primera aparición de un carácter de `str` que pertenece al conjunto de caracteres de `strCharSet`.  En la búsqueda no se incluye el carácter nulo de finalización.  
  
 `wcspbrk` y `_mbspbrk` son versiones de caracteres anchos y multibyte de `strpbrk`.  Los argumentos y el valor devuelto de `wcspbrk` son cadenas de caracteres anchos; los de `_mbspbrk` son cadenas de caracteres multibyte.  
  
 `_mbspbrk` valida sus parámetros.  Si `str` o `strCharSet` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbspbrk` devuelve `NULL` y establece `errno` en `EINVAL`.  `strpbrk` y `wcspbrk` no validan sus parámetros.  Estas tres funciones se comportan exactamente igual.  
  
 `_mbspbrk` es igual que `_mbscspn`, salvo que `_mbspbrk` devuelve un puntero en lugar de un valor de tipo [size\_t](../../c-runtime-library/standard-types.md).  
  
 En C, estas funciones toman un puntero `const` como primer argumento.  En C\+\+, hay disponibles dos sobrecargas.  La sobrecarga que toma un puntero a `const` devuelve un puntero a `const`; la versión que contiene un puntero a un valor que no es `const` devuelve un puntero a un valor que no es `const`.  La macro \_CONST\_CORRECT\_OVERLOADS se define si están disponibles tanto las versiones `const` como no `const` de estas funciones.  Si necesita un comportamiento que no sea `const` para ambas sobrecargas de C\+\+, defina el símbolo \_CONST\_RETURN.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional. Para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; la versión con el sufijo `_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcspbrk`|`strpbrk`|`_mbspbrk`|`wcspbrk`|  
|**no disponible**|**no disponible**|`_mbspbrk_l`|**no disponible**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strpbrk`|\<string.h\>|  
|`wcspbrk`|\<string.h\> o \<wchar.h\>|  
|`_mbspbrk`, `_mbspbrk_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strpbrk.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The 3 men and 2 boys ate 5 pigs\n";  
   char *result = NULL;  
  
   // Return pointer to first digit in "string".  
   printf( "1: %s\n", string );  
   result = strpbrk( string, "0123456789" );  
   printf( "2: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "3: %s\n", result++ );  
   result = strpbrk( result, "0123456789" );  
   printf( "4: %s\n", result );  
}  
```  
  
  **1: The 3 men and 2 boys ate 5 pigs**  
**2: 3 men and 2 boys ate 5 pigs**  
**3: 2 boys ate 5 pigs**  
**4: 5 pigs**   
## Equivalente en .NET Framework  
 [System::String::IndexOfAny](https://msdn.microsoft.com/en-us/library/system.string.indexofany.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn, wcscspn, \_mbscspn, \_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strchr, wcschr, \_mbschr, \_mbschr\_l](../../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)