---
title: "wcrtomb_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcrtomb_s"
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
  - "wcrtomb_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "caracteres anchos, convertir"
  - "wcrtomb_s (función)"
  - "caracteres multibyte"
  - "caracteres, convertir"
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# wcrtomb_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convertir un carácter ancho en su representación de carácter multibyte. Una versión de [wcrtomb](../../c-runtime-library/reference/wcrtomb.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char *mbchar,  
   size_t sizeOfmbchar,  
   wchar_t *wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char (&mbchar)[size],  
   wchar_t *wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `pReturnValue`  
 Devuelve el número de bytes escritos o \-1 si se produjo un error.  
  
 \[out\] `mbchar`  
 El resultante multibyte convierte caracteres.  
  
 \[in\] `sizeOfmbchar`  
 El tamaño de la `mbchar` variable en bytes.  
  
 \[in\] `wchar`  
 Carácter ancho que se va a convertir.  
  
 \[in\] `mbstate`  
 Puntero a un objeto `mbstate_t`.  
  
## Valor devuelto  
 Devuelve cero o una `errno` valor si se produce un error.  
  
## Comentarios  
 El `wcrtomb_s` función convierte un carácter ancho, comenzando en el estado de conversión especificado contenido en `mbstate`, desde el valor contenido en `wchar`, en la dirección representada por `mbchar`. El `pReturnValue` valor será el número de bytes que se convierten, pero no más de `MB_CUR_MAX` bytes o un \-1 si se produjo un error.  
  
 Si `mbstate` es null, interno `mbstate_t` se utiliza el estado de la conversión. Si el carácter que se encuentra en `wchar` no tiene un carácter multibyte correspondiente, el valor de `pReturnValue` será \-1 y la función devolverá la `errno` valor de `EILSEQ`.  
  
 El `wcrtomb_s` función difiere de [wctomb\_s, \_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md) por su capacidad de reinicio. El estado de la conversión se almacena en `mbstate` para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación utilizaría `wcsrlen` en lugar de `wcslen`, si una llamada subsiguiente a `wcsrtombs_s` se utiliza en lugar de `wcstombs_s.`  
  
 En C\+\+, con esta función se simplifica mediante sobrecargas de plantilla; las sobrecargas pueden deducir la longitud de búfer automáticamente \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Excepciones  
 El `wcrtomb_s` función es segura para subprocesos siempre y cuando no llama a ninguna función en el subproceso actual `setlocale` mientras se está ejecutando esta función y el `mbstate` es null.  
  
## Ejemplo  
  
```  
// crt_wcrtomb_s.c  
// This program converts a wide character  
// to its corresponding multibyte character.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    errno_t     returnValue;  
    size_t      pReturnValue;  
    mbstate_t   mbstate;  
    size_t      sizeOfmbStr = 1;  
    char        mbchar = 0;  
    wchar_t*    wchar = L"Q\0";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),  
                            *wchar, &mbstate);  
    if (returnValue == 0) {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wchar);  
        printf(" was converted to a the \"%c\" ", mbchar);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
```Output  
El carácter ancho correspondiente "Q" se convirtió en un carácter multibyte "Q".  
```  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wcrtomb_s`|\<wchar.h\>|  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)