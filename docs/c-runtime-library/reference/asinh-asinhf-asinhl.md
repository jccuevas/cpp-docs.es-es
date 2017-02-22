---
title: "asinh, asinhf, asinhl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "asinh"
  - "asinhf"
  - "asinhl"
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
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "asinhf"
  - "asinhl"
  - "asinh"
dev_langs: 
  - "C++"
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# asinh, asinhf, asinhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el seno hiperbólico inverso.  
  
## Sintaxis  
  
```  
double asinh(    double x  ); float asinh(    float x  );  // C++ only long double asinh(    long double x );  // C++ only float asinhf(    float x  ); long double asinhl(    long double x );  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
## Valor devuelto  
 Las funciones `asinh` devuelven el seno hiperbólico inverso \(arcoseno hiperbólico\) de `x`.  Esta función es válida en el dominio de punto flotante.  El valor devuelto es el mismo si `x` es un NaN reservado, indefinido o infinito.  
  
|Entrada|Excepción SEH|Excepción de `_matherr`|  
|-------------|-------------------|-----------------------------|  
|± QNAN, IND, INF|ninguna|ninguna|  
  
## Comentarios  
 Cuando se usa C\+\+, se puede llamar a las sobrecargas de `asinh` que toman y devuelven los valores `float` o `long double`.  En un programa C, `asinh` siempre toma y devuelve un tipo `double`.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`asinh`, `asinhf`, `asinhl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```c  
// crt_asinh.c  
// Compile by using: cl /W4 crt_asinh.c  
// This program displays the hyperbolic sine of pi / 4  
// and the arc hyperbolic sine of the result.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = sinh( pi / 4 );  
   y = asinh( x );  
   printf( "sinh( %f ) = %f\n", pi/4, x );  
   printf( "asinh( %f ) = %f\n", x, y );  
}  
```  
  
  **sinh\(0,785398\) \= 0,868671**  
**asinh\( 0.868671 \) \= 0.785398**   
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Long double](../../misc/long-double.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [acosh, acoshf, acoshl](../../c-runtime-library/reference/acosh-acoshf-acoshl.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [atanh, atanhf, atanhl](../../c-runtime-library/reference/atanh-atanhf-atanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)