---
title: "_mbclen, mblen, _mblen_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbclen"
  - "mblen"
  - "_mblen_l"
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
  - "mblen"
  - "ftclen"
  - "_mbclen"
  - "tclen"
  - "_ftclen"
  - "_tclen"
  - "mbclen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbclen (función)"
  - "_mblen_l (función)"
  - "_tclen (función)"
  - "mbclen (función)"
  - "mblen (función)"
  - "mblen_l (función)"
  - "tclen (función)"
ms.assetid: d5eb92a0-b7a3-464a-aaf7-9890a8e3ed70
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _mbclen, mblen, _mblen_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la longitud y determina la validez de un carácter multibyte.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
size_t _mbclen(  
   const unsigned char *c   
);  
int mblen(  
   const char *mbstr,  
   size_t count   
);  
int _mblen_l(  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter multibyte.  
  
 `mbstr`  
 Dirección de una secuencia de bytes de caracteres multibyte.  
  
 `count`  
 Número de bytes que se va a comprobar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_mbclen` devuelve 1 o 2, en función de que el carácter multibyte `c` tenga una longitud de 1 o 2 bytes.  `_mbclen` no devuelve ningún error.  Si `mbstr` no es `NULL`, `mblen` devuelve la longitud, en bytes, del carácter multibyte.  Si `mbstr` es `NULL` o señala al carácter nulo de caracteres anchos, `mblen` devuelve 0.  Si el objeto al que señala `mbstr` no forma un carácter multibyte válido en los primeros `count` caracteres, `mblen` devuelve –1.  
  
## Comentarios  
 La función `_mbclen` devuelve la longitud, en bytes, del carácter multibyte `c`.  Si `c` no señala al byte inicial de un carácter multibyte determinado por una llamada implícita a `_ismbblead`, el resultado de `_mbclen` es imprevisible.  
  
 `mblen` devuelve la longitud en bytes de `mbstr` si es un carácter multibyte válido, y determina la validez del carácter multibyte asociada a la página de códigos.  `mblen` examina `count` bytes o menos de `mbstr`, pero no más `MB_CUR_MAX` bytes.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tclen`|Se asigna a una macro o una función insertada|`_mbclen`|Se asigna a una macro o una función insertada|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbclen`|\<mbstring.h\>|  
|`mblen`|\<stdlib.h\>|  
|`_mblen_l`|\<stdlib.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_mblen.c  
/* illustrates the behavior of the mblen function  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    int      i;  
    char    *pmbc = (char *)malloc( sizeof( char ) );  
    wchar_t  wc   = L'a';  
  
    printf( "Convert wide character to multibyte character:\n" );  
    wctomb_s( &i, pmbc, sizeof(char), wc );  
    printf( "  Characters converted: %u\n", i );  
    printf( "  Multibyte character: %x\n\n", *pmbc );  
  
    i = mblen( pmbc, MB_CUR_MAX );  
    printf( "Length in bytes of multibyte character %x: %u\n", *pmbc, i );  
  
    pmbc = NULL;  
    i = mblen( pmbc, MB_CUR_MAX );  
    printf( "Length in bytes of NULL multibyte character %x: %u\n", pmbc, i );  
}  
```  
  
## Resultados  
  
```  
Convert wide character to multibyte character:  
  Characters converted: 1  
  Multibyte character: 61  
  
Length in bytes of multibyte character 61: 1  
Length in bytes of NULL multibyte character 0: 0  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbccpy, \_mbccpy\_l](../../c-runtime-library/reference/mbccpy-mbccpy-l.md)   
 [strlen, wcslen, \_mbslen, \_mbslen\_l, \_mbstrlen, \_mbstrlen\_l](../../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)