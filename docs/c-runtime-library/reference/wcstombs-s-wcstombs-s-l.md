---
title: "wcstombs_s, _wcstombs_s_l | Microsoft Docs"
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
  - "_wcstombs_s_l"
  - "wcstombs_s"
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
  - "wcstombs_s"
  - "_wcstombs_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcstombs_s (función)"
  - "conversión de cadenas, caracteres anchos"
  - "caracteres anchos, convertir"
  - "_wcstombs_s_l (función)"
  - "wcstombs_s_l (función)"
  - "caracteres, convertir"
  - "conversión de cadenas, cadenas de caracteres multibyte"
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: 31
caps.handback.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wcstombs_s, _wcstombs_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una secuencia de caracteres anchos a una secuencia de caracteres multibyte correspondiente. Una versión de [wcstombs, \_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count   
);  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `pReturnValue`  
 El número de caracteres convertidos.  
  
 \[out\] `mbstr`  
 La dirección de un búfer para la cadena de caracteres multibyte convertido resultante.  
  
 \[in\]`sizeInBytes`  
 El tamaño en bytes de la `mbstr` búfer.  
  
 \[in\] `wcstr`  
 Puntos de la cadena de caracteres anchos que se va a convertir.  
  
 \[in\] `count`  
 El número máximo de bytes que se va a almacenar en el `mbstr` búfer, sin incluir el carácter nulo de terminación o [\_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 \[in\] `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
|Condición de error|Valor devuelto y `errno`|  
|------------------------|------------------------------|  
|`mbstr` es `NULL` y `sizeInBytes` \> 0|`EINVAL`|  
|`wcstr` es `NULL`|`EINVAL`|  
|El búfer de destino es demasiado pequeño para contener la cadena convertida \(a menos que `count` es `_TRUNCATE`; vea la sección comentarios que aparece a continuación\)|`ERANGE`|  
  
 Si ocurre alguna de estas condiciones, se invoca la excepción de parámetro no válido como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si se permite que la ejecución continúe, la función devuelve un código de error y establece `errno` como se indica en la tabla.  
  
## Comentarios  
 El `wcstombs_s` función convierte una cadena de caracteres anchos señalada `wcstr` en caracteres multibyte almacenados en el búfer señalado por `mbstr`. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:  
  
-   Se encontró un carácter ancho nulo  
  
-   Se encontró un carácter ancho que no se puede convertir  
  
-   El número de bytes almacenados en el `mbstr` búfer es igual a `count`.  
  
 La cadena de destino siempre está terminada en null \(incluso en el caso de un error\).  
  
 Si `count` es el valor especial [\_TRUNCATE](../../c-runtime-library/truncate.md), a continuación, `wcstombs_s` convierte tanto de la cadena como caber en el búfer de destino, dejando espacio para un terminador null.  
  
 Si `wcstombs_s` convierte correctamente la cadena de origen, pone el tamaño en bytes de la cadena convertida, incluido el terminador nulo, en `*``pReturnValue` \(proporcionan `pReturnValue` no es `NULL`\). Esto ocurre incluso si la `mbstr` argumento es `NULL` y proporciona una manera de determinar el tamaño de búfer necesario. Observe que si `mbstr` es `NULL`, `count` se omite.  
  
 Si `wcstombs_s` encuentra un carácter ancho no se puede convertir en un carácter multibyte, pone en 0 `*``pReturnValue`, Establece el búfer de destino en una cadena vacía, establece `errno` a `EILSEQ`, y devuelve `EILSEQ`.  
  
 Si las secuencias señaladas por `wcstr` y `mbstr` se superponen, el comportamiento de `wcstombs_s` no está definido.  
  
> [!IMPORTANT]
>  Asegúrese de que `wcstr` y `mbstr` no se superponen y que `count` refleja correctamente el número de caracteres anchos a convertir.  
  
 `wcstombs_s` utiliza la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; `_wcstombs_s_l` es idéntico a `wcstombs` salvo que usa la configuración regional que se pasa en su lugar. Para obtener más información, consulta [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina el requisito de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wcstombs_s`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Este programa muestra el comportamiento de la `wcstombs_s` \(función\).  
  
```  
// crt_wcstombs_s.c  
// This example converts a wide character  
// string to a multibyte character string.  
#include <stdio.h>  
#include <stdlib.h>  
#include <assert.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t   i;  
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t*pWCBuffer = L"Hello, world.";  
  
    printf( "Convert wide-character string:\n" );  
  
    // Conversion  
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,   
               pWCBuffer, (size_t)BUFFER_SIZE );  
  
    // Output  
    printf("   Characters converted: %u\n", i);  
    printf("    Multibyte character: %s\n\n",  
     pMBBuffer );  
  
    // Free multibyte character buffer  
    if (pMBBuffer)  
    {  
    free(pMBBuffer);  
    }  
}  
```  
  
```Output  
Convertir la cadena de caracteres anchos: caracteres convertidos: 14 caracteres Multibyte: Hello, world.  
```  
  
## Equivalente en .NET Framework  
 No disponible. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_mbclen, mblen, \_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, \_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, \_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb\_s, \_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)