---
title: "mbstowcs, _mbstowcs_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "mbstowcs"
  - "_mbstowcs_l"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbstowcs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbstowcs_l (función)"
  - "mbstowcs (función)"
  - "mbstowcs_l (función)"
ms.assetid: 96696b27-e068-4eeb-8006-3f7a0546ae6d
caps.latest.revision: 30
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mbstowcs, _mbstowcs_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una secuencia de caracteres multibyte en una secuencia correspondiente de caracteres anchos.  Hay disponibles versiones más seguras de estas funciones; vea [mbstowcs\_s, \_mbstowcs\_s\_l](../../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md).  
  
## Sintaxis  
  
```  
size_t mbstowcs(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count   
);  
size_t _mbstowcs_l(  
   wchar_t *wcstr,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t mbstowcs(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _mbstowcs_l(  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `wcstr`  
 La dirección de una secuencia de caracteres anchos.  
  
 \[in\] `mbstr`  
 La dirección de una secuencia de null finalizó caracteres multibyte.  
  
 \[in\] `count`  
 El número máximo de caracteres multibyte a convertir.  
  
 \[in\] `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Si `mbstowcs` convierte correctamente la cadena de origen, devuelve el número de caracteres convertidos multibyte.  Si el argumento de `wcstr` es `NULL`, la función devuelve el tamaño necesario \(en caracteres anchos\) de la cadena de destino.  Si `mbstowcs` encuentra un carácter no válido multibyte, devuelve – 1.  Si el valor devuelto es `count`, la cadena de caracteres no termina en null.  
  
> [!IMPORTANT]
>  Asegúrese de que `wcstr` y `mbstr` no se superpongan, y que `count` correctamente refleja el número de caracteres multibyte convertir.  
  
## Comentarios  
 La función de `mbstowcs` convierte hasta un número máximo de caracteres multibyte de `count` indicada por `mbstr` en una cadena de caracteres anchos correspondientes que están determinados por la configuración regional actual.  Almacena la cadena de caracteres resultante en la dirección representada por *`wcstr`.* El resultado es similar a una serie de llamadas a `mbtowc`.  Si `mbstowcs` encuentra el carácter null de solo\- byte \(“\\0”\) o antes o cuando `count` aparece, convierte el carácter null a un carácter null de caracteres anchos \(L'\\0\) y se detiene.  Así la cadena de caracteres en `wcstr` terminado en null solo si un carácter null se encuentra durante la conversión.  Si las secuencias designadas por a `wcstr` y la superposición de `mbstr` , el comportamiento no están definidas.  
  
 Si el argumento de `wcstr` es `NULL`, `mbstowcs` devuelve el número de caracteres anchos que resultarían de conversión, sin incluir un carácter null final.  La cadena de origen debe ser terminado en null para el valor correcto que se devolverá.  Si necesita la cadena de caracteres anchos resultante hacer en null, agregue uno al valor devuelto.  
  
 Si el argumento de `mbstr` es `NULL`, o si `count` es \>`INT_MAX`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) .  Si la ejecución puede continuar, el errno se establece en `EINVAL` y la función devuelve \-1.  
  
 `mbstowcs` utiliza la configuración regional actual para cualquier comportamiento configuración regional\-dependiente; `_mbstowcs_l` es idéntico pero utiliza la configuración regional pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`mbstowcs`|\<stdlib.h\>|  
|`_mbstowcs_l`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_mbstowcs.c  
// compile with: /W3  
// illustrates the behavior of the mbstowcs function  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main( void )  
{  
    size_t size;  
    int nChar = 2; // number of characters to convert  
    int requiredSize;  
  
    unsigned char    *pmbnull  = NULL;  
    unsigned char    *pmbhello = NULL;  
    char* localeInfo;  
  
    wchar_t *pwchello = L"\x3042\x3043"; // 2 Hiragana characters  
    wchar_t *pwc;  
  
    /* Enable the Japanese locale and codepage */  
    localeInfo = setlocale(LC_ALL, "Japanese_Japan.932");  
    printf("Locale information set to %s\n", localeInfo);  
  
    printf( "Convert to multibyte string:\n" );  
  
    requiredSize = wcstombs( NULL, pwchello, 0); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    printf("  Required Size: %d\n", requiredSize);  
  
    /* Add one to leave room for the null terminator. */  
    pmbhello = (unsigned char *)malloc( requiredSize + 1);  
    if (! pmbhello)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = wcstombs( pmbhello, pwchello, requiredSize + 1); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s  
    if (size == (size_t) (-1))  
    {  
        printf("Couldn't convert string. Code page 932 may"  
                " not be available.\n");  
        return 1;  
    }  
    printf( "  Number of bytes written to multibyte string: %u\n",  
            (unsigned int) size );  
    printf( "  Hex values of the " );  
    printf( " multibyte characters: %#.2x %#.2x %#.2x %#.2x\n",  
            pmbhello[0], pmbhello[1], pmbhello[2], pmbhello[3] );  
    printf( "  Codepage 932 uses 0x81 to 0x9f as lead bytes.\n\n");  
  
    printf( "Convert back to wide-character string:\n" );  
  
    /* Assume we don't know the length of the multibyte string.  
     Get the required size in characters, and allocate enough space. */  
  
    requiredSize = mbstowcs(NULL, pmbhello, 0); // C4996  
    /* Add one to leave room for the NULL terminator */  
    pwc = (wchar_t *)malloc( (requiredSize + 1) * sizeof( wchar_t ));  
    if (! pwc)  
    {  
        printf("Memory allocation failure.\n");  
        return 1;  
    }  
    size = mbstowcs( pwc, pmbhello, requiredSize + 1); // C4996  
    if (size == (size_t) (-1))  
    {  
       printf("Couldn't convert string--invalid multibyte character.\n");  
    }  
    printf( "  Characters converted: %u\n", (unsigned int)size );  
    printf( "  Hex value of first 2" );  
    printf( " wide characters: %#.4x %#.4x\n\n", pwc[0], pwc[1] );  
    free(pwc);  
    free(pmbhello);  
}  
```  
  
  **Información de configuración regional establecida en Japanese\_Japan.932**  
**Convierte en la cadena multibyte:**  
 **Tamaño necesarios: 4**  
 **Número de bytes escritos en la cadena multibyte: 4**  
 **Valores hexadecimales de caracteres multibyte: 0x82 0xa0 0x82 0xa1**  
 **La página de códigos 932 utiliza 0x81 a 0x9f como bytes iniciales.**  
**Convierte a cadena de caracteres:**  
 **Caracteres convertidos: 2**  
 **Valor hexadecimal de los primeros 2 caracteres anchos: 0x3042 0x3043**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen, mblen, \_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc, \_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs, \_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb, \_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)