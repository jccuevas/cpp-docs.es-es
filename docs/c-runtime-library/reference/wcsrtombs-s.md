---
title: "wcsrtombs_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcsrtombs_s"
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
  - "wcsrtombs_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conversión de cadenas, caracteres anchos"
  - "wcsrtombs_s (función)"
  - "caracteres anchos, cadenas"
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# wcsrtombs_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena de caracteres anchos en su representación de cadena de caracteres multibyte.  Una versión de [wcsrtombs](../../c-runtime-library/reference/wcsrtombs.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `pReturnValue`  
 El número de caracteres convertido.  
  
 \[out\] `mbstr`  
 La dirección de un búfer para producir convirtió la cadena de caracteres multibyte.  
  
 \[out\] `sizeInBytes`  
 Tamaño en bytes del búfer de `mbstr` .  
  
 \[in\] `wcstr`  
 Apunta a la cadena de caracteres anchos que se va a convertir.  
  
 \[in\] `count`  
 El número de bytes máximo que se almacenan en el búfer de `mbstr` , o [\_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 \[in\] `mbstate`  
 Un puntero a un objeto de estado de la conversión de `mbstate_t` .  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
|Condición de error|Valor devuelto y `errno`|  
|------------------------|------------------------------|  
|`mbstr` es `NULL` y `sizeInBytes` \> 0|`EINVAL`|  
|El valor de `wcstr` es `NULL`.|`EINVAL`|  
|El búfer de destino es demasiado pequeño para contener la cadena convertida \(a menos que `count` es `_TRUNCATE`; vea las notas siguiente\)|`ERANGE`|  
  
 Si cualquiera de estas condiciones aparecen, la excepción no válida de parámetros se invoca como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) .  Si la ejecución puede continuar, la función devuelve un código de error y establece `errno` como se indica en la tabla.  
  
## Comentarios  
 La función de `wcsrtombs_s` convierte una cadena de caracteres anchos indicada por `wcstr` en caracteres multibyte almacenados en el búfer indicada por `mbstr`, utilizando el estado de conversión contenida en `mbstate`.  La conversión continuará por cada carácter hasta que una de estas condiciones se cumple:  
  
-   Se encuentra un carácter ancho null  
  
-   Se encuentra un carácter ancho que no puede convertirse  
  
-   El número de bytes almacenados en el búfer de `mbstr` es igual a `count`.  
  
 La cadena de destino siempre es terminada en null \(incluso en el caso de un error\).  
  
 Si `count` es el valor especial [\_TRUNCATE](../../c-runtime-library/truncate.md), después `wcsrtombs_s` convierte tanto de la cadena que caben en el búfer de destino, mientras todavía deja el sitio para un carácter null final.  
  
 Si `wcsrtombs_s` convierte correctamente la cadena de origen, coloca el tamaño en bytes de la cadena convertida, incluido el terminador nulo, en `*``pReturnValue` \( `pReturnValue` proporcionado no es `NULL`\).  Esto hace que incluso si el argumento de `mbstr` es `NULL` y proporciona una manera de determinar el tamaño de búfer requerido.  Tenga en cuenta que si `mbstr` es `NULL`, `count` se omite.  
  
 Si `wcsrtombs_s` encuentra un carácter ancho que no puede convertir un carácter multibyte, coloca \-1 en `*``pReturnValue`, establece el búfer de destino en una cadena vacía, establece `errno` a `EILSEQ`, y devuelve `EILSEQ`.  
  
 Si las secuencias designadas por a `wcstr` y la superposición de `mbstr` , el comportamiento de `wcsrtombs_s` no están definidas.  `wcsrtombs_s` afecta a la categoría de LC\_TYPE de la configuración regional actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `wcstr` y `mbstr` no se superpongan, y que `count` correctamente refleja el número de caracteres anchos convertir.  
  
 La función de `wcsrtombs_s` diferencia de [wcstombs\_s, \_wcstombs\_s\_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md) por su restartability.  Almacena el estado de la conversión en `mbstate` para las llamadas subsiguientes igual o a otras funciones reiniciables.  Los resultados son indefinidos al mezclar el uso de funciones reiniciables y nonrestartable.  Por ejemplo, una aplicación utilizaría `wcsrlen` en lugar de `wcslen`, si una llamada subsiguiente a `wcsrtombs_s` se utilizó en lugar de `wcstombs_s.`  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Excepciones  
 La función de `wcsrtombs_s` es seguro multiproceso a ninguna función en el subproceso actual llame a `setlocale` mientras esta función se ejecuta y `mbstate` es null.  
  
## Ejemplo  
  
```  
// crt_wcsrtombs_s.cpp  
//   
// This code example converts a wide  
// character string into a multibyte  
// character string.  
//  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
void main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    errno_t         err;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,  
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);  
    if (err == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfully converted.\n" );  
    }  
}  
```  
  
  **La cadena se convierte correctamente.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wcsrtombs_s`|\<wchar.h\>|  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb\_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb, \_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs, \_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)