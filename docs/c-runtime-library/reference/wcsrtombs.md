---
title: "wcsrtombs | Microsoft Docs"
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
  - "wcsrtombs"
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
  - "wcsrtombs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcsrtombs (función)"
  - "conversión de cadenas, caracteres anchos"
  - "caracteres anchos, cadenas"
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcsrtombs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena de caracteres anchos en su representación de cadena de caracteres multibyte.  Una versión más segura de esta función está disponible; vea [wcsrtombs\_s](../../c-runtime-library/reference/wcsrtombs-s.md).  
  
## Sintaxis  
  
```  
size_t wcsrtombs(  
   char *mbstr,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcsrtombs(  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `mbstr`  
 La ubicación de la dirección de la cadena de caracteres convertida resultante multibyte.  
  
 \[in\] `wcstr`  
 Indirectamente señala a la ubicación de la cadena de caracteres anchos que se va a convertir.  
  
 \[in\] `count`  
 El número de caracteres que se va a convertir.  
  
 \[in\] `mbstate`  
 Un puntero a un objeto de estado de la conversión de `mbstate_t` .  
  
## Valor devuelto  
 Devuelve el número de bytes convierten correctamente, sin incluir null que finaliza el byte null \(si existe\), si no es un \-1 si se ha producido un error.  
  
## Comentarios  
 La función de `wcsrtombs` convierte una cadena de caracteres anchos, comenzando en el estado especificado de conversión contenida en `mbstate`, de resaltado indirecto de los valores en `wcstr`, en la dirección de `mbstr`.  La conversión continuará por cada carácter hasta: después de que se encuentra un carácter ancho final nulo, cuando se encuentra un carácter no correspondiente o cuando el carácter siguiente superaría el límite contenido en `count`.  Si `wcsrtombs` encuentra el carácter null de caracteres anchos \(L'\\0\) o antes o cuando `count` aparece, se convierte en un 0 de 8 bits y detiene.  
  
 Así, la cadena de caracteres multibyte en `mbstr` terminado en null solo si `wcsrtombs` encuentra un carácter null de caracteres anchos durante la conversión.  Si las secuencias designadas por a `wcstr` y la superposición de `mbstr` , el comportamiento de `wcsrtombs` no están definidas.  `wcsrtombs` afecta a la categoría de LC\_TYPE de la configuración regional actual.  
  
 La función de `wcsrtombs` diferencia de [wcstombs, \_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) por su restartability.  Almacena el estado de la conversión en `mbstate` para las llamadas subsiguientes igual o a otras funciones reiniciables.  Los resultados son indefinidos al mezclar el uso de funciones reiniciables y nonrestartable.  Por ejemplo, una aplicación utilizaría `wcsrlen` en lugar de `wcsnlen`, si una llamada subsiguiente a `wcsrtombs` se utilizó en lugar de `wcstombs`.  
  
 Si el argumento de `mbstr` es `NULL`, `wcsrtombs` devuelve el tamaño necesario en bytes de la cadena de destino.  Si `mbstate` es null, utilizan el estado interno de la conversión de `mbstate_t` .  Si la secuencia `wchar` de carácter no tiene una representación de caracteres correspondiente multibyte, se devuelve \-1 y `errno` se establece en `EILSEQ`.  
  
 En C\+\+, esta función tiene una sobrecarga de plantilla que invoca según el nuevo, garantizar el equivalente de esta función.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Excepciones  
 La función de `wcsrtombs` es seguro multiproceso a ninguna función en el subproceso actual llame a `setlocale` mientras esta función se ejecuta y `mbstate` no es null.  
  
## Ejemplo  
  
```  
// crt_wcsrtombs.cpp  
// compile with: /W3  
// This code example converts a wide  
// character string into a multibyte  
// character string.  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
int main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    countConverted = wcsrtombs(mbString, &wcsIndirectString,  
                               MB_BUFFER_SIZE, &mbstate); // C4996  
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s  
    if (errno == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfuly converted.\n" );  
    }  
}  
```  
  
  **La cadena se convierte correctamente.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wcsrtombs`|\<wchar.h\>|  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb, \_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs, \_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)