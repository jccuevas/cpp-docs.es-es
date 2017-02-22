---
title: "_strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsspnp"
  - "_wcsspnp"
  - "_mbsspnp_l"
  - "_strspnp"
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
  - "_tcsspnp"
  - "_mbsspnp"
  - "strspnp"
  - "_ftcsspnp"
  - "_mbsspnp_l"
  - "wcsspnp"
  - "mbsspnp_l"
  - "_wcsspnp"
  - "_strspnp"
  - "mbsspnp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsspnp (función)"
  - "_mbsspnp_l (función)"
  - "_strspnp (función)"
  - "_tcsspnp (función)"
  - "_wcsspnp (función)"
  - "mbsspnp (función)"
  - "mbsspnp_l (función)"
  - "strspnp (función)"
  - "tcsspnp (función)"
  - "wcsspnp (función)"
ms.assetid: 1ce18100-2edd-4c3b-af8b-53f204d80233
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _strspnp, _wcsspnp, _mbsspnp, _mbsspnp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve un puntero al primer carácter de una cadena determinada que no esté en otra cadena determinada.  
  
> [!IMPORTANT]
>  `_mbsspnp` y `_mbsspnp_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strspnp(  
   const char *str,  
   const char *charset  
);  
wchar_t *_wcsspnp(  
   const unsigned wchar_t *str,  
   const unsigned wchar_t *charset  
);  
unsigned char *_mbsspnp(  
   const unsigned char *str,  
   const unsigned char *charset  
);  
unsigned char *_mbsspnp_l(  
   const unsigned char *str,  
   const unsigned char *charset,  
   _locale_t locale  
);  
  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL que se va a buscar.  
  
 `charset`  
 Juego de caracteres terminado en NULL.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_strspnp`, `_wcsspnp` y `_mbsspnp` devuelven un puntero al primer carácter de `str` que no pertenezca al conjunto de caracteres de `charset`*.* Cada una de estas funciones devuelve `NULL` si todos los caracteres de `str` están en `charset`*.* Para cada una de estas rutinas, no hay ningún valor devuelto reservado para indicar un error.  
  
## Comentarios  
 La función `_mbsspnp` devuelve un puntero al carácter multibyte que es el primer carácter de `str` que no pertenece al conjunto de caracteres de `charset`.  `_mbsspnp` reconoce las secuencias de caracteres multibyte de acuerdo con la [página de códigos multibyte](../../c-runtime-library/code-pages.md) actualmente en uso.  En la búsqueda no se incluyen los caracteres nulos de finalización.  
  
 Si `str` o `charset` es un puntero nulo, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `NULL` y establece en `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsspnp`|`_strspnp`|`_mbsspnp`|`_wcsspnp`|  
  
 `_strspnp` y `_wcsspnp` son versiones de caracteres de un solo byte y caracteres anchos de `_mbsspnp`.  Por lo demás, `_strspnp` y `_wcsspnp` se comportan de forma idéntica a `_mbsspnp`. Se proporcionan solo para esta asignación y no se deben usar por ninguna otra razón.  Para obtener más información, vea [Usar asignaciones de texto genérico](../../c-runtime-library/using-generic-text-mappings.md) y [Asignaciones de texto genérico](../../c-runtime-library/generic-text-mappings.md).  
  
 `_mbsspnp_l` es exactamente igual, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsspnp`|\<mbstring.h\>|  
|`_strspnp`|\<tchar.h\>|  
|`_wcsspnp`|\<tchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_mbsspnp.c  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void ) {  
   const unsigned char string1[] = "cabbage";  
   const unsigned char string2[] = "c";  
   unsigned char *ptr = 0;  
   ptr = _mbsspnp( string1, string2 );  
   printf( "%s\n", ptr);  
}  
```  
  
## Resultados  
  
```  
abbage  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)   
 [strncat\_s, \_strncat\_s\_l, wcsncat\_s, \_wcsncat\_s\_l, \_mbsncat\_s, \_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)