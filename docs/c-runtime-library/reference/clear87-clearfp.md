---
title: "_clear87, _clearfp | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_clearfp"
  - "_clear87"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "clearfp"
  - "_clearfp"
  - "_clear87"
  - "clear87"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_clear87 (función)"
  - "_clearfp (función)"
  - "clear87 (función)"
  - "clearfp (función)"
  - "borrar palabra de estado de punto flotante"
ms.assetid: 72d24a70-7688-4793-ae09-c96d33fcca52
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _clear87, _clearfp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene y borra la palabra de estado de punto flotante.  
  
## Sintaxis  
  
```  
unsigned int _clear87( void );  
unsigned int _clearfp( void );  
```  
  
## Valor devuelto  
 Los bits del valor devuelto indican el estado de punto flotante antes de llamar a `_clear87` o a `_clearfp`.  Para ver una definición completa de los bits que devuelve `_clear87`, vea Float.h.  Muchas de las funciones de la biblioteca matemática modifican la palabra de estado 8087\/80287 con resultados imprevisibles.  Los valores devueltos de `_clear87` y `_status87` son más confiables si se realizan menos operaciones de punto flotante entre estados conocidos de la palabra de estado de punto flotante.  
  
## Comentarios  
 La función `_clear87` borra las marcas de excepción de la palabra de estado de punto flotante, establece el bit de actividad en 0 y devuelve la palabra de estado.  La palabra de estado de punto flotante es una combinación de la palabra de estado 8087\/80287 y de otras condiciones detectadas por el controlador de excepciones 8087\/80287 \(por ejemplo, el desbordamiento y subdesbordamiento de la pila de punto flotante\).  
  
 `_clearfp` es una versión portátil e independiente de la plataforma de la rutina `_clear87`.  Es idéntica a `_clear87` en plataformas Intel \(x86\) y también es compatible con las plataformas x64 y ARM.  Para asegurarse de que el código de punto flotante se puede llevar a x64 y a ARM, use `_clearfp`.  Si solo va a usar plataformas x86, puede usar `_clear87` o `_clearfp`.  
  
 Estas funciones están en desuso cuando se compilan con [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) o `/clr:pure` porque Common Language Runtime solo admite la precisión de punto flotante predeterminada.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_clear87`|\<float.h\>|  
|`_clearfp`|\<float.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_clear87.c  
// compile with: /Od  
  
// This program creates various floating-point   
// problems, then uses _clear87 to report on these problems.  
// Compile this program with Optimizations disabled (/Od).   
// Otherwise the optimizer will remove the code associated with   
// the unused floating-point values.  
//  
  
#include <stdio.h>  
#include <float.h>  
  
int main( void )  
{  
   double a = 1e-40, b;  
   float x, y;  
  
   printf( "Status: %.4x - clear\n", _clear87()  );  
  
   // Store into y is inexact and underflows:  
   y = a;  
   printf( "Status: %.4x - inexact, underflow\n", _clear87() );  
  
   // y is denormal:   
   b = y;  
   printf( "Status: %.4x - denormal\n", _clear87() );  
}  
```  
  
  **Status: 0000 \- clear**  
**Status: 0003 \- inexact, underflow**  
**Status: 80000 \- denormal**   
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_control87, \_controlfp, \_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)   
 [\_status87, \_statusfp, \_statusfp2](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)