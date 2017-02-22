---
title: "_memicmp, _memicmp_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_memicmp_l"
  - "_memicmp"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_memicmp"
  - "memicmp_l"
  - "_memicmp_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_memicmp (función)"
  - "_memicmp_l (función)"
  - "memicmp (función)"
  - "memicmp_l (función)"
ms.assetid: 0a6eb945-4077-4f84-935d-1aaebe8db8cb
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _memicmp, _memicmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara los caracteres de dos búferes \(sin distinción entre mayúsculas y minúsculas\).  
  
## Sintaxis  
  
```  
int _memicmp(  
   const void *buf1,  
   const void *buf2,  
   size_t count   
);  
int _memicmp_l(  
   const void *buf1,  
   const void *buf2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `buf1`  
 Primer búfer.  
  
 `buf2`  
 Segundo búfer.  
  
 `count`  
 Número de caracteres.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 El valor devuelto indica la relación entre los búferes.  
  
|Valor devuelto|Relación de los primeros bytes del número de buf1 y de buf2|  
|--------------------|-----------------------------------------------------------------|  
|\< 0|`buf1` menos que `buf2`.|  
|0|`buf1` idéntico a `buf2`.|  
|\> 0|`buf1` es mayor que `buf2`.|  
|`_NLSCMPERROR`|Error.|  
  
## Comentarios  
 La función de `_memicmp` compara los primeros caracteres de `count` de los dos búferes `buf1` y de byte `buf2` por byte.  La comparación no distingue entre mayúsculas y minúsculas.  
  
 Si `buf1` o `buf2` es un puntero NULL, esta función invoca un controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `_NLSCMPERROR` y establece en `errno` en `EINVAL`.  
  
 `_memicmp` utiliza la configuración regional actual para el comportamiento configuración regional\-dependiente; `_memicmp_l` es idéntico pero utiliza la configuración regional pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_memicmp`|\<memory.h\> o \<string.h\>|  
|`_memicmp_l`|\<memory.h\> o \<string.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_memicmp.c  
// This program uses _memicmp to compare  
// the first 29 letters of the strings named first and  
// second without regard to the case of the letters.  
  
#include <memory.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   int result;  
   char first[] = "Those Who Will Not Learn from History";  
   char second[] = "THOSE WHO WILL NOT LEARN FROM their mistakes";  
   // Note that the 29th character is right here ^  
  
   printf( "Compare '%.29s' to '%.29s'\n", first, second );  
   result = _memicmp( first, second, 29 );  
   if( result < 0 )  
      printf( "First is less than second.\n" );  
   else if( result == 0 )  
      printf( "First is equal to second.\n" );  
   else if( result > 0 )  
      printf( "First is greater than second.\n" );  
}  
```  
  
  **Comparar a “Está Will Not Learn de Those de” a WILL NOT LEARN FROM de WHO de THOSE”**  
**Primero es igual a segundo.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [\_stricmp, \_wcsicmp, \_mbsicmp, \_stricmp\_l, \_wcsicmp\_l, \_mbsicmp\_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)