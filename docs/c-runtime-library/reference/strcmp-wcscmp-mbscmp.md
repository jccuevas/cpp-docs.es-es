---
title: "strcmp, wcscmp, _mbscmp | Microsoft Docs"
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
  - "wcscmp"
  - "_mbscmp"
  - "strcmp"
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
  - "_mbscmp"
  - "wcscmp"
  - "strcmp"
  - "_tcscmp"
  - "_ftcscmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcscmp (función)"
  - "_mbscmp (función)"
  - "_tcscmp (función)"
  - "ftcscmp (función)"
  - "mbscmp (función)"
  - "strcmp (función)"
  - "comparación de cadenas [C++]"
  - "cadenas [C++], comparar"
  - "tcscmp (función)"
  - "wcscmp (función)"
ms.assetid: 5d216b57-7a5c-4cb3-abf0-0f4facf4396d
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcmp, wcscmp, _mbscmp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara cadenas.  
  
> [!IMPORTANT]
>  `_mbscmp` no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int strcmp(  
   const char *string1,  
   const char *string2   
);  
int wcscmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbscmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
```  
  
#### Parámetros  
 `string1`, `string2`  
 Cadenas terminadas en NULL que se van a comparar.  
  
## Valor devuelto  
 El valor devuelto para cada una de estas funciones indica la relación ordinal de `string1` respecto a `string2`.  
  
|Valor|Relación de string1 y string2|  
|-----------|-----------------------------------|  
|\< 0|`string1` es menor que `string2`.|  
|0|`string1` es idéntica a `string2`.|  
|\> 0|`string1` es mayor que `string2`.|  
  
 Si se produce un error de validación de parámetros `_mbscmp` devuelve `_NLSCMPERROR`, que se define en \<string.h\> y \<mbstring.h\>.  
  
## Comentarios  
 La función `strcmp` realiza una comparación ordinal de `string1` y `string2` y devuelve un valor que indica su relación.  `wcscmp` y `_mbscmp` son, respectivamente, versiones de caracteres anchos y multibyte de `strcmp`.  `_mbscmp` reconoce secuencias de caracteres multibyte según la página actual de códigos multibyte y devuelve `_NLSCMPERROR` cuando se produce un error.  Para obtener más información, vea [Páginas de códigos](../../c-runtime-library/code-pages.md).  Además, si `string1` o `string2` es un puntero nulo, `_mbscmp` invoca el controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbscmp` devuelve `_NLSCMPERROR` y establece `errno` en `EINVAL`.  `strcmp` y `wcscmp` no validan sus parámetros.  Estas tres funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcscmp`|`strcmp`|`_mbscmp`|`wcscmp`|  
  
 Las funciones `strcmp` se diferencian de las funciones `strcoll` en que las comparaciones de `strcmp` son ordinales y no se ven afectadas por la configuración regional.  `strcoll` compara las cadenas de manera lexicográfica usando la categoría `LC_COLLATE` de la configuración regional actual.  Para obtener más información sobre la categoría `LC_COLLATE`, vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  
  
 En la configuración regional "C", el orden de los caracteres del juego de caracteres \(juego de caracteres ASCII\) es el mismo que en los caracteres lexicográficos.  Sin embargo, en otras configuraciones regionales, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico.  Por ejemplo, en algunas configuraciones regionales europeas el carácter “a” \(valor 0x61\) precede el carácter “ä” \(valor 0xE4\) en el juego de caracteres, pero el carácter “ä” precede el carácter “a” lexicográficamente.  
  
 En las configuraciones regionales en las que el orden del juego de caracteres y el lexicográfico difieran, puede usar `strcoll` en lugar de `strcmp` para realizar la comparación lexicográfica de cadenas.  Como alternativa, puede usar `strxfrm` en las cadenas originales y después usar `strcmp` en las cadenas resultantes.  
  
 Las funciones `strcmp` distinguen entre mayúsculas y minúsculas.  `_stricmp`, `_wcsicmp` y `_mbsicmp` comparan cadenas convirtiéndolas primero en su forma minúscula.  Dos cadenas que contiene caracteres situados entre “Z” y “a” en la tabla ASCII \(“\[”, “`\`”, “\]”', “`^`”, “`_`” y “```”\) se comparan de forma distinta, dependiendo de si son mayúsculas o minúsculas.  Por ejemplo, las dos cadenas `"ABCDE"` y `"ABCD^"` se comparan de un modo si la comparación es minúscula \(`"abcde"` \> `"abcd^"`\) y del otro \(`"ABCDE"` \< `"ABCD^"`\) si la comparación es mayúscula.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strcmp`|\<string.h\>|  
|`wcscmp`|\<string.h\> o \<wchar.h\>|  
|`_mbscmp`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_strcmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof (tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof (tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof (tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
  **Cadenas de la comparación:**  
 **The quick brown dog jumps over the lazy fox**  
 **The QUICK brown dog jumps over the lazy fox**  
 **strcmp:   La cadena 1 es mayor que la cadena 2**  
 **\_stricmp:  La cadena 1 es igual a la cadena 2**   
## Equivalente en .NET Framework  
 [System::String::CompareOrdinal](https://msdn.microsoft.com/en-us/library/system.string.compareordinal.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [\_memicmp, \_memicmp\_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [\_stricmp, \_wcsicmp, \_mbsicmp, \_stricmp\_l, \_wcsicmp\_l, \_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strxfrm, wcsxfrm, \_strxfrm\_l, \_wcsxfrm\_l](../../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)