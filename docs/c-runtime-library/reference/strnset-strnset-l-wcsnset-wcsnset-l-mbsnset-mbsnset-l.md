---
title: "_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnset"
  - "_strnset"
  - "_mbsnset_l"
  - "_wcsnset_l"
  - "_wcsnset"
  - "_strnset_l"
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
  - "_tcsncset_l"
  - "mbsnset_l"
  - "_tcsnset_l"
  - "_fstrnset"
  - "_wcsnset_l"
  - "_ftcsnset"
  - "wcsnset_l"
  - "_mbsnset_l"
  - "_strnset"
  - "_tcsnset"
  - "_strnset_l"
  - "mbsnset"
  - "strnset_l"
  - "_mbsnset"
  - "_wcsnset"
  - "_tcsncset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fstrnset (función)"
  - "_ftcsnset (función)"
  - "_mbsnset (función)"
  - "_mbsnset_l (función)"
  - "_strnset (función)"
  - "_strnset_l (función)"
  - "_tcsncset (función)"
  - "_tcsncset_l (función)"
  - "_tcsnset (función)"
  - "_tcsnset_l (función)"
  - "_wcsnset (función)"
  - "_wcsnset_l (función)"
  - "caracteres [C++], inicializar en formatos"
  - "fstrnset (función)"
  - "ftcsnset (función)"
  - "inicializar caracteres"
  - "mbsnset (función)"
  - "mbsnset_l (función)"
  - "cadenas [C++], inicializar"
  - "strnset_l (función)"
  - "tcsncset (función)"
  - "tcsnset (función)"
  - "tcsnset_l (función)"
  - "wcsnset_l (función)"
ms.assetid: 3f306489-5763-48e5-b939-aefee7c94ef5
caps.latest.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# _strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Inicializa los caracteres de una cadena en un carácter dado.  Existen versiones más seguras de estas funciones; vea [\_strnset\_s, \_strnset\_s\_l, \_wcsnset\_s, \_wcsnset\_s\_l, \_mbsnset\_s, \_mbsnset\_s\_l](../../c-runtime-library/reference/strnset-s-strnset-s-l-wcsnset-s-wcsnset-s-l-mbsnset-s-mbsnset-s-l.md).  
  
> [!IMPORTANT]
>  `_mbsnset` y `_mbsnset_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strnset(  
   char *str,  
   int c,  
   size_t count   
);  
char *_strnset_l(  
   char *str,  
   int c,  
   size_t count,  
   locale_t locale  
);  
wchar_t *_wcsnset(  
   wchar_t *str,  
   wchar_t c,  
   size_t count   
);  
wchar_t *_wcsnset_l(  
   wchar_t *str,  
   wchar_t c,  
   size_t count,  
   _locale_t locale  
);  
unsigned char *_mbsnset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnset_l(  
   unsigned char *str,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `str`  
 Cadena que se va a modificar.  
  
 `c`  
 Especificación de carácter.  
  
 `count`  
 Número de caracteres que se va a establecer.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero a la cadena modificada.  
  
## Comentarios  
 La función `_strnset`  establece, como máximo, los primeros `count` caracteres de `str` en `c` \(convertidos en `char`\).  Si `count` es mayor que la longitud de `str`, se usa la longitud de `str` en lugar de `count`.  
  
 `_wcsnset` y `_mbsnset`  son versiones de caracteres anchos y multibyte de `_strnset`.  Los argumentos de cadena y el valor devuelto de `_wcsnset`  son cadenas de caracteres anchos; los de `_mbsnset` son cadenas de caracteres multibyte.  Estas tres funciones se comportan exactamente igual.  
  
 `_mbsnset` valida sus parámetros; si `str` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbsnset`  devuelve NULL y establece `errno`  en `EINVAL`.  `_strnset` y `_wcsnset` no validan sus parámetros.  
  
 El valor de la categoría `LC_CTYPE`  de la configuración regional afecta al valor de salida; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strnset`|\<string.h\>|  
|`_strnset_l`|\<tchar.h\>|  
|`_wcsnset`|\<string.h\> o \<wchar.h\>|  
|`_wcsnset_l`|\<tchar.h\>|  
|`_mbsnset`, `_mbsnset_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strnset.c  
// compile with: /W3  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 characters of string to be *'s */  
   printf( "Before: %s\n", string );  
   _strnset( string, '*', 4 ); // C4996  
   // Note: _strnset is deprecated; consider using _strnset_s  
   printf( "After:  %s\n", string );  
}  
```  
  
  **Antes: This is a test**  
**Después: \*\*\*\* is a test**   
## Equivalente en .NET Framework  
 [System::String::Replace](https://msdn.microsoft.com/en-us/library/system.string.replace.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)