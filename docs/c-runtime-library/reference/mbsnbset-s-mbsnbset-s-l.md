---
title: "_mbsnbset_s, _mbsnbset_s_l | Microsoft Docs"
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
  - "_mbsnbset_s_l"
  - "_mbsnbset_s"
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
  - "mbsnbset_s"
  - "_mbsnbset_s_l"
  - "_mbsnbset_s"
  - "mbsnbset_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbset_s (función)"
  - "_mbsnbset_s_l (función)"
  - "_tcsnset_s (función)"
  - "_tcsnset_s_l (función)"
  - "mbsnbset_s (función)"
  - "mbsnbset_s_l (función)"
  - "tcsnset_s (función)"
  - "tcsnset_s_l (función)"
ms.assetid: 811f92c9-cc31-4bbd-8017-2d1bfc6fb96f
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbset_s, _mbsnbset_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece los primeros `n` bytes de una cadena de caracteres multibyte en un carácter especificado.  Estas versiones de [\_mbsnbset, \_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md) incluyen mejoras de seguridad, como se describe en el tema sobre las [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t _mbsnbset_s(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count   
);  
errno_t _mbsnbset_s_l(  
   unsigned char *str,  
   size_t size,  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbset_s(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbset_s_l(  
   unsigned char (&str)[size],  
   unsigned int c,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena que se va a modificar.  
  
 `size`  
 Tamaño del búfer de cadena.  
  
 `c`  
 Valor del carácter de un solo byte o multibyte.  
  
 `count`  
 Número de bytes que se van a establecer.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cero si es correcto; en caso contrario, código de error.  
  
## Comentarios  
 Las funciones `_mbsnbset_s` y `_mbsnbset_s_l` establecen, como máximo, los primeros `count` bytes de `str` en `c`.  Si `count` es mayor que la longitud de `str`, se usa la longitud de `str` en lugar de `count`.  Si `c` es un carácter multibyte y no se puede establecer totalmente en el último byte especificado por `count`, el último byte se completa con un carácter en blanco.  `_mbsnbset_s` y `_mbsnbset_s_l` no colocan un carácter de terminación nulo al final de `str`.  
  
 `_mbsnbset_s` y `_mbsnbset_s_l` son similares a `_mbsnset`, salvo en que establecen `count` bytes en lugar de `count` caracteres de `c`.  
  
 Si `str` es `NULL` o `count` es cero, esta función genera una excepción de parámetro no válido, como se describe en el tema sobre [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`.  Además, si `c` no es un carácter multibyte válido, `errno` se establece en `EINVAL` y se usa un espacio en su lugar.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  La versión `_mbsnbset_s` de esta función usa la configuración regional actual de su comportamiento dependiente de la configuración regional; la versión `_mbsnbset_s_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir automáticamente la longitud del búfer, lo que elimina la necesidad de especificar un argumento de tamaño.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnset_s`|`_strnset_s`|`_mbsnbset_s`|`_wcsnset_s`|  
|`_tcsnset_s_l`|`_strnset_s _l`|`_mbsnbset_s_l`|`_wcsnset_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnbset_s`|\<mbstring.h\>|  
|`_mbsnbset_s_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_mbsnbset_s.c  
#include <mbstring.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[15] = "This is a test";  
   /* Set not more than 4 bytes of string to be *'s */  
   printf( "Before: %s\n", string );  
   _mbsnbset_s( string, sizeof(string), '*', 4 );  
   printf( "After:  %s\n", string );  
}  
```  
  
## Salida  
  **Antes: This is a test**  
**Después: \*\*\*\* is a test**   
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat, \_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_strnset, \_strnset\_l, \_wcsnset, \_wcsnset\_l, \_mbsnset, \_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)