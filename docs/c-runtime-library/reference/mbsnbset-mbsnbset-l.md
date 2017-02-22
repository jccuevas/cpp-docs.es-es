---
title: "_mbsnbset, _mbsnbset_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbset"
  - "_mbsnbset_l"
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
  - "mbsnbset"
  - "mbsnbset_l"
  - "_mbsnbset"
  - "_mbsnbset_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbset (función)"
  - "_mbsnbset_l (función)"
  - "_tcsnset (función)"
  - "_tcsnset_l (función)"
  - "mbsnbset (función)"
  - "mbsnbset_l (función)"
  - "tcsnset (función)"
  - "tcsnset_l (función)"
ms.assetid: 8e46ef75-9a56-42d2-a522-a08450c67c19
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _mbsnbset, _mbsnbset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece los primeros `n` bytes de una cadena de caracteres multibyte en un carácter especificado.  Hay disponibles versiones más seguras de estas funciones; vea [\_mbsnbset\_s, \_mbsnbset\_s\_l](../../c-runtime-library/reference/mbsnbset-s-mbsnbset-s-l.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned char *_mbsnbset(  
   unsigned char *str,  
   unsigned int c,  
   size_t count   
);  
unsigned char *_mbsnbset_l(  
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
 Valor del carácter de un solo byte o multibyte.  
  
 `count`  
 Número de bytes que se van a establecer.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_mbsnbset` devuelve un puntero a la cadena modificada.  
  
## Comentarios  
 Las funciones `_mbsnbset` y `_mbsnbset_l` establecen, como máximo, los primeros `count` bytes de `str` en `c`.  Si `count` es mayor que la longitud de `str`, se usa la longitud de `str` en lugar de `count`.  Si `c` es un carácter multibyte y no se puede establecer totalmente en el último byte especificado por `count`, el último byte se completa con un carácter en blanco.  `_mbsnbset` y `_mbsnbset_l`no colocan un carácter de terminación nulo al final de `str`.  
  
 `_mbsnbset` y `_mbsnbset_l`son parecidas a `_mbsnset`, salvo que establecen los `count` bytes en lugar de `count` caracteres de `c`.  
  
 Si `str` es `NULL` o `count` es cero, esta función genera una excepción de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  Además, si `c` no es un carácter multibyte válido, `errno` se establece en `EINVAL` y se usa un espacio en su lugar.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  La versión `_mbsnbset` de esta función usa la configuración regional actual de su comportamiento dependiente de la configuración regional; la versión `_mbsnbset_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 **Nota de seguridad** Esta API crea la posible amenaza de un problema de saturación del búfer.  Los problemas de saturación del búfer son un método frecuente de ataque del sistema, que produce una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnset`|`_strnset`|`_mbsnbset`|`_wcsnset`|  
|`_tcsnset_l`|`_strnset_l`|`_mbsnbset_l`|`_wcsnset_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnbset`|\<mbstring.h\>|  
|`_mbsnbset_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_mbsnbset.c  
// compile with: /W3  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset( string, '*', 4 ); // C4996  
   // Note; _mbsnbset is deprecated; consider _mbsnbset_s  
   printf( "After:  %s\n", string );  
}  
```  
  
## Resultados  
  
```  
Before: This is a test  
After:  **** is a test  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat, \_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_strnset, \_strnset\_l, \_wcsnset, \_wcsnset\_l, \_mbsnset, \_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)