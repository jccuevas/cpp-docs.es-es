---
title: "wcrtomb | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcrtomb"
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
  - "wcrtomb"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "caracteres, convertir"
  - "caracteres multibyte"
  - "wcrtomb (función)"
  - "caracteres anchos, convertir"
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# wcrtomb
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un carácter ancho en su representación de caracteres multibyte.  Una versión más segura de esta función está disponible; vea [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md).  
  
## Sintaxis  
  
```  
size_t wcrtomb(  
   char *mbchar,  
   wchar_t wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcrtomb(  
   char (&mbchar)[size],  
   wchar_t wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `mbchar`  
 El carácter convertidos multibyte resultante.  
  
 \[in\] `wchar`  
 Un carácter ancho a convertir.  
  
 \[in\] `mbstate`  
 Puntero a un objeto `mbstate_t`.  
  
## Valor devuelto  
 Devuelve el número de bytes necesarios para representar el carácter convertido multibyte, si no es un \-1 si se produce un error.  
  
## Comentarios  
 La función de `wcrtomb` convierte un carácter ancho, comenzando en el estado especificado de conversión contenida en `mbstate`, el valor contenido en `wchar`, en la dirección representada por `mbchar`.  El valor devuelto es el número de bytes necesarios para representar el carácter correspondiente multibyte, pero no devolverá más que los bytes de `MB_CUR_MAX` .  
  
 Si `mbstate` es null, el objeto interno de `mbstate_t` que contiene el estado de la conversión de `mbchar` se utiliza.  Si la secuencia `wchar` de carácter no tiene una representación de caracteres correspondiente multibyte, se devuelve \-1 y `errno` se establece en `EILSEQ`.  
  
 La función de `wcrtomb` diferencia de [wctomb, \_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) por su restartability.  Almacena el estado de la conversión en `mbstate` para las llamadas subsiguientes igual o a otras funciones reiniciables.  Los resultados son indefinidos al mezclar el uso de funciones reiniciables y nonrestartable.  Por ejemplo, una aplicación utilizaría `wcsrlen` en lugar de `wcsnlen`, si una llamada subsiguiente a `wcsrtombs` se utilizó en lugar de `wcstombs`.  
  
 En C\+\+, esta función tiene una sobrecarga de plantilla que invoca según el nuevo, asegúrese homólogos de esta función.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Excepciones  
 La función de `wcrtomb` es seguro multiproceso a ninguna función en el subproceso actual llame a `setlocale` mientras esta función se ejecuta mientras `mbstate` es null.  
  
## Ejemplo  
  
```  
// crt_wcrtomb.c  
// compile with: /W3  
// This program converts a wide character  
// to its corresponding multibyte character.  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    size_t      sizeOfCovertion = 0;  
    mbstate_t   mbstate;  
    char        mbStr = 0;  
    wchar_t*    wcStr = L"Q";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996  
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead  
    if (sizeOfCovertion > 0)  
    {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wcStr);  
        printf(" was converted to the \"%c\" ", mbStr);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
  **El carácter ancho correspondiente “q” se convierte al carácter multibyte de “q”.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wcrtomb`|\<wchar.h\>|  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)