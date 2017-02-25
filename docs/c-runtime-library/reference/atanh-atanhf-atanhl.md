---
title: "atanh, atanhf, atanhl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "atanhl"
  - "atanhf"
  - "atanh"
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
  - "atanhl"
  - "atanhf"
  - "atanh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "atanh (función)"
  - "atanhf (función)"
  - "atanhl (función)"
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# atanh, atanhf, atanhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula la tangente hiperbólica inversa.  
  
## Sintaxis  
  
```  
double atanh(    double x  ); float atanh(    float x  );  // C++ only long double atanh(    long double x );  // C++ only float atanhf(    float x  ); long double atanhl(    long double x );  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
## Valor devuelto  
 Las funciones `atanh` devuelven la tangente hiperbólica inversa \(arcotangente hiperbólica\) de `x`.  Si `x` es mayor que 1 o menor que \-1, `errno` se establece en `EDOM` y el resultado es un NaN reservado.  Si `x` equivale a 1 o \-1, se devuelve un valor infinito positivo o negativo respectivamente, y `errno` se establece en `ERANGE`.  
  
|Entrada|Excepción SEH|Excepción de `Matherr`|  
|-------------|-------------------|----------------------------|  
|± QNAN,IND|ninguna|ninguna|  
|`X` ≥ 1; `x` ≤ \-1|ninguna|ninguna|  
  
## Comentarios  
 Puesto que C\+\+ permite las sobrecargas, es posible llamar a las sobrecargas de `atanh` que toman y devuelven los valores `float` o `long double`.  En un programa C, `atanh` siempre toma y devuelve un tipo `double`.  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`atanh`, `atanhf`, `atanhl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_atanh.c  
// This program displays the hyperbolic tangent of pi / 4  
// and the arc hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tanh( pi / 4 );  
   y = atanh( x );  
   printf( "tanh( %f ) = %f\n", pi/4, x );  
   printf( "atanh( %f ) = %f\n", x, y );  
}  
```  
  
  **tanh\( 0,785398 \) \= 0,655794**  
**atanh\( 0.655794 \) \= 0.785398**   
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Long double](../../misc/long-double.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)