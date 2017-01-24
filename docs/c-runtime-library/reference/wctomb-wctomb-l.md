---
title: "wctomb, _wctomb_l | Microsoft Docs"
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
  - "_wctomb_l"
  - "wctomb"
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
  - "wctomb"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wctomb_l (función)"
  - "caracteres, convertir"
  - "conversión de cadenas, cadenas de carácter multibyte"
  - "conversión de cadenas, caracteres anchos"
  - "wctomb (función)"
  - "wctomb_l (función)"
  - "caracteres anchos, convertir"
ms.assetid: 4a543f0e-5516-4d81-8ff2-3c5206f02ed5
caps.latest.revision: 23
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# wctomb, _wctomb_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un carácter ancho al carácter correspondiente multibyte.  Hay disponibles versiones más seguras de estas funciones; vea [wctomb\_s, \_wctomb\_s\_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md).  
  
## Sintaxis  
  
```  
int wctomb(  
   char *mbchar,  
   wchar_t wchar   
);  
int _wctomb_l(  
   char *mbchar,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `mbchar`  
 La dirección de un carácter multibyte.  
  
 `wchar`  
 Un carácter ancho.  
  
## Valor devuelto  
 Si `wctomb` convierte el carácter ancho a un carácter multibyte, devuelve el número de bytes \(que nunca es mayor que `MB_CUR_MAX`\) en el carácter ancho.  Si `wchar` es el carácter null de caracteres anchos \(L'\\0\), `wctomb` devuelve 1.  Si el puntero `mbchar` de destino es NULL, `wctomb` devuelve 0.  Si la conversión no es posible en la configuración regional actual, `wctomb` vuelve – 1 y `errno` se establece en `EILSEQ`.  
  
## Comentarios  
 La función de `wctomb` convierte su argumento de `wchar` el carácter correspondiente multibyte y almacena el resultado en `mbchar`.  Puede llamar a la función de cualquier punto de cualquier programa.  `wctomb` utiliza la configuración regional actual para cualquier comportamiento configuración regional\-dependiente; `_wctomb_l` es idéntico a `wctomb` pero utiliza la configuración regional pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 `wctomb` valida sus parámetros.  Si `mbchar` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve \-1.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wctomb`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Este programa muestra el comportamiento de la función de wctomb.  
  
```  
// crt_wctomb.cpp  
// compile with: /W3  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int i;  
   wchar_t wc = L'a';  
   char *pmb = (char *)malloc( MB_CUR_MAX );  
  
   printf( "Convert a wide character:\n" );  
   i = wctomb( pmb, wc ); // C4996  
   // Note: wctomb is deprecated; consider using wctomb_s  
   printf( "   Characters converted: %u\n", i );  
   printf( "   Multibyte character: %.1s\n\n", pmb );  
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