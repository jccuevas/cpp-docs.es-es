---
title: "acosh, acoshf, acoshl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "acoshf"
  - "acosh"
  - "acoshl"
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
  - "acosh"
  - "acoshf"
  - "acoshl"
  - "math/acosh"
  - "math/acoshf"
  - "math/acoshl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acoshf (función)"
  - "acosh (función)"
  - "acoshl (función)"
ms.assetid: 6985c4d7-9e2a-44ce-9a9b-5a43015f15f7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# acosh, acoshf, acoshl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el coseno hiperbólico inverso.  
  
## Sintaxis  
  
```  
double acosh(  
   double x   
);  
float acosh(  
   float x   
);  // C++ only  
long double acosh(  
   long double x  
);  // C++ only  
float acoshf(  
   float x   
);  
long double acoshl(  
   long double x  
);  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
## Valor devuelto  
 Las funciones `acosh` devuelven el coseno hiperbólico inverso \(arco coseno hiperbólico\) de `x`. Estas funciones son válidas en el dominio `x` ≥ 1. Si `x` es menor que 1, `errno` se establece en `EDOM` y el resultado es un NaN reservado. El valor devuelto es el mismo si `x` es un NaN reservado, indefinido o infinito.  
  
|Entrada|Excepción SEH|Excepción de `_matherr`|  
|-------------|-------------------|-----------------------------|  
|± QNAN, IND, INF|ninguna|ninguna|  
|x \< 1|ninguna|ninguna|  
  
## Comentarios  
 Cuando se usa C\+\+, se puede llamar a las sobrecargas de `acosh` que toman y devuelven los valores `float` o `long double`. En un programa C, `acosh` siempre toma y devuelve un tipo `double`.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`acosh`, `acoshf`, `acoshl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```c  
// crt_acosh.c  
// Compile by using: cl /W4 crt_acosh.c  
// This program displays the hyperbolic cosine of pi / 4  
// and the arc hyperbolic cosine of the result.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = cosh( pi / 4 );  
   y = acosh( x );  
   printf( "cosh( %f ) = %f\n", pi/4, x );  
   printf( "acosh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
cosh( 0.785398 ) = 1.324609 acosh( 1.324609 ) = 0.785398  
```  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Long double](../../misc/long-double.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [asinh, asinhf, asinhl](../../c-runtime-library/reference/asinh-asinhf-asinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [atanh, atanhf, atanhl](../../c-runtime-library/reference/atanh-atanhf-atanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)