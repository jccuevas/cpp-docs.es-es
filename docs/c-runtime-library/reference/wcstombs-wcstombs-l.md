---
title: "wcstombs, _wcstombs_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcstombs"
  - "_wcstombs_l"
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
  - "wcstombs"
  - "_wcstombs_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_wcstombs_l (función)"
  - "caracteres, convertir"
  - "conversión de cadenas, cadenas de carácter multibyte"
  - "conversión de cadenas, caracteres anchos"
  - "wcstombs (función)"
  - "wcstombs_l (función)"
  - "caracteres anchos, convertir"
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# wcstombs, _wcstombs_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una secuencia de caracteres anchos a una secuencia correspondiente de caracteres multibyte.  Hay disponibles versiones más seguras de estas funciones; vea [wcstombs\_s, \_wcstombs\_s\_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md).  
  
## Sintaxis  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `mbstr`  
 La dirección de una secuencia de caracteres multibyte.  
  
 `wcstr`  
 La dirección de una secuencia de caracteres anchos.  
  
 `count`  
 El número de bytes máximo que pueden almacenarse en la cadena de salida multibyte.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Si `wcstombs` convierte correctamente la cadena multibyte, devuelve el número de bytes escritos en la cadena de salida multibyte, excepto `NULL` que finaliza \(si existe\).  Si el argumento de `mbstr` es `NULL`, `wcstombs` devuelve el tamaño necesario en bytes de la cadena de destino.  Si `wcstombs` encuentra un carácter ancho que no puede convertir un carácter multibyte, devuelve – 1 echado para escribir `size_t` y establece `errno` a `EILSEQ`.  
  
## Comentarios  
 La función de `wcstombs` convierte la cadena de caracteres designada por a `wcstr` a los caracteres correspondientes multibyte y almacena los resultados en la matriz de `mbstr` .  El parámetro de `count` indica el número de bytes máximo que se pueden almacenar en la cadena de salida multibyte \(es decir, el tamaño de `mbstr`\).  No se suelen conocer cuántos bytes se necesarios al convertir una cadena de caracteres.  Algunos caracteres anchos requieren un solo byte en la cadena de salida; otros requieren dos.  Si hay dos bytes en la cadena de salida multibyte por cada carácter ancho en la cadena de entrada \(carácter ancho incluidos `NULL`\), el resultado se garantiza para ajustarse.  
  
 Si `wcstombs` encuentra el carácter null de caracteres anchos \(L'\\0\) o antes o cuando `count` aparece, se convierte en un 0 de 8 bits y detiene.  Así, la cadena de caracteres multibyte en `mbstr` terminado en null solo si `wcstombs` encuentra un carácter null de caracteres anchos durante la conversión.  Si las secuencias designadas por a `wcstr` y la superposición de `mbstr` , el comportamiento de `wcstombs` no están definidas.  
  
 Si el argumento de `mbstr` es `NULL`, `wcstombs` devuelve el tamaño necesario en bytes de la cadena de destino.  
  
 `wcstombs` valida sus parámetros.  Si `wcstr` es `NULL`, o si `count` es mayor que`INT_MAX`, esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) .  Si la ejecución puede continuar, la función establece `errno` a `EINVAL` y devuelve \-1.  
  
 `wcstombs` utiliza la configuración regional actual para cualquier comportamiento configuración regional\-dependiente; `_wcstombs_l` es idéntico pero utiliza la configuración regional pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wcstombs`|\<stdlib.h\>|  
|`_wcstombs_l`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Este programa muestra el comportamiento de la función de `wcstombs` .  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
  **Cadena de caracteres convert:**  
 **Caracteres convertidos: 13**  
 **Carácter de Multibyte: Hello, world.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_mbclen, mblen, \_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, \_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, \_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb, \_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)