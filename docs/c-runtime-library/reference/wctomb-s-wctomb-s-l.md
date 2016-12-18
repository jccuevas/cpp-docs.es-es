---
title: "wctomb_s, _wctomb_s_l | Microsoft Docs"
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
  - "_wctomb_s_l"
  - "wctomb_s"
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
  - "wctomb_s"
  - "_wctomb_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wctomb_s_l (función)"
  - "caracteres, convertir"
  - "conversión de cadenas, cadenas de carácter multibyte"
  - "conversión de cadenas, caracteres anchos"
  - "wctomb_s (función)"
  - "wctomb_s_l (función)"
  - "caracteres anchos, convertir"
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wctomb_s, _wctomb_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un carácter ancho al carácter correspondiente multibyte.  Una versión de [wctomb, \_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 \[out\] `pRetValue`  
 El número de bytes, o código que indica el resultado.  
  
 \[out\] `mbchar`  
 La dirección de un carácter multibyte.  
  
 \[in\] `sizeInBytes`  
 Tamaño del búfer `mbchar`.  
  
 \[in\] `wchar`  
 Un carácter ancho.  
  
 \[in\] `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
 Condiciones de error  
  
|`mbchar`|`sizeInBytes`|Valor devuelto|`pRetValue`|  
|--------------|-------------------|--------------------|-----------------|  
|`NULL`|\>0|`EINVAL`|no modificado|  
|any|\>`INT_MAX`|`EINVAL`|no modificado|  
|any|demasiado pequeño|`EINVAL`|no modificado|  
  
 Si es un de los sobre condiciones de error, el controlador no válido de parámetro se invoca, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `wctomb` devuelve `EINVAL` y establece `errno` en `EINVAL`.  
  
## Comentarios  
 La función de `wctomb_s` convierte su argumento de `wchar` el carácter correspondiente multibyte y almacena el resultado en `mbchar`.  Puede llamar a la función de cualquier punto de cualquier programa.  
  
 Si `wctomb_s` convierte el carácter ancho a un carácter multibyte, coloca el número de bytes \(que nunca es mayor que `MB_CUR_MAX`\) en el carácter ancho en integer indicada por `pRetValue`.  Si `wchar` es el carácter null de caracteres anchos \(L'\\0\), `wctomb_s` rellena `pRetValue` con 1.  Si el puntero `mbchar` de destino es NULL, `wctomb_s` coloca 0 en `pRetValue`.  Si la conversión no es posible en la configuración regional actual, `wctomb_s` coloca – 1 en `pRetValue`.  
  
 `wctomb_s` utiliza la configuración regional actual para la información configuración regional\-dependiente; `_wctomb_s_l` es idéntico pero utiliza la configuración regional pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wctomb_s`|\<stdlib.h\>|  
|`_wctomb_s_l`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Este programa muestra el comportamiento de la función de `wctomb` .  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
  **Convierte un carácter ancho:**  
 **Caracteres convertidos: 1**  
 **Carácter de Multibyte: t**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_mbclen, mblen, \_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, \_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, \_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs, \_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)