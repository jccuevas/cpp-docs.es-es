---
title: "strspn, wcsspn, _mbsspn, _mbsspn_l | Microsoft Docs"
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
  - "_mbsspn_l"
  - "wcsspn"
  - "strspn"
  - "_mbsspn"
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
  - "_ftcsspn"
  - "wcsspn"
  - "_mbsspn"
  - "_tcsspn"
  - "strspn"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcsspn (función)"
  - "_mbsspn (función)"
  - "_mbsspn_l (función)"
  - "_tcsspn (función)"
  - "ftcsspn (función)"
  - "mbsspn (función)"
  - "mbsspn_l (función)"
  - "cadenas [C++], buscar"
  - "strspn (función)"
  - "subcadenas, buscar"
  - "tcsspn (función)"
  - "wcsspn (función)"
ms.assetid: d077284a-809f-4068-959e-c6d6262677eb
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strspn, wcsspn, _mbsspn, _mbsspn_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve, en una cadena, el índice del primer carácter que no pertenece a un juego de caracteres.  
  
> [!IMPORTANT]
>  `_mbsspn` y `_mbsspn_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
size_t strspn(  
   const char *str,  
   const char *strCharSet   
);  
size_t wcsspn(  
   const wchar_t *str,  
   const wchar_t *strCharSet   
);  
size_t _mbsspn(  
   const unsigned char *str,  
   const unsigned char *strCharSet   
);  
size_t _mbsspn_l(  
   const unsigned char *str,  
   const unsigned char *strCharSet,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL que se va a buscar.  
  
 `strCharSet`  
 Juego de caracteres terminado en NULL.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un valor entero que especifica la longitud de la subcadena de `str` formada totalmente por caracteres de `strCharSet`*.* Si `str` empieza con un carácter que no está en `strCharSet`*,* la función devuelve 0.  
  
## Comentarios  
 La función `strspn` devuelve el índice del primer carácter de `str` que no pertenece al juego de caracteres de `strCharSet`.  En la búsqueda no se incluyen los caracteres nulos de finalización.  
  
 `wcsspn` y `_mbsspn` son versiones de caracteres anchos y multibyte de `strspn`**.** Los argumentos de `wcsspn` son cadenas de caracteres anchos; los de `_mbsspn` son cadenas de caracteres multibyte.  `_mbsspn` valida sus parámetros.  Si `str` o `strCharSet` es`NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbspn` establece `errno` en `EINVAL` y devuelve 0.  `strspn` y `wcsspn` no validan sus parámetros.  Estas tres funciones se comportan exactamente igual.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsspn`|`strspn`|`_mbsspn`|`wcsspn`|  
|**no disponible**|**no disponible**|`_mbsspn_l`|**no disponible**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strspn`|\<string.h\>|  
|`wcsspn`|\<string.h\> o \<wchar.h\>|  
|`_mbsspn`, `_mbsspn_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strspn.c  
// This program uses strspn to determine  
// the length of the segment in the string "cabbage"  
// consisting of a's, b's, and c's. In other words,  
// it finds the first non-abc letter.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[] = "cabbage";  
   int  result;  
   result = strspn( string, "abc" );  
   printf( "The portion of '%s' containing only a, b, or c "  
           "is %d bytes long\n", string, result );  
}  
```  
  
  **The portion of 'cabbage' containing only a, b, or c is 5 bytes long**   
## Equivalente en .NET Framework  
 [System::String::Substring](https://msdn.microsoft.com/en-us/library/system.string.substring.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strspnp, \_wcsspnp, \_mbsspnp, \_mbsspnp\_l](../../c-runtime-library/reference/strspnp-wcsspnp-mbsspnp-mbsspnp-l.md)   
 [strcspn, wcscspn, \_mbscspn, \_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)