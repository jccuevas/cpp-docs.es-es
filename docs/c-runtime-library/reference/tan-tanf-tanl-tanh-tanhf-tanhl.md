---
title: "tan, tanf, tanl, tanh, tanhf, tanhl | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "tanhf"
  - "tanh"
  - "tan"
  - "tanhl"
  - "tanf"
  - "tanl"
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
  - "tanh"
  - "tan"
  - "_tanl"
  - "tanl"
  - "_tanhl"
  - "tanf"
  - "tanhf"
  - "tanhl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "tanl (función)"
  - "tanhl (función)"
  - "_tanl (función)"
  - "_tanhl (función)"
  - "tan (función)"
  - "calcular tangentes"
  - "tangente"
  - "tanh (función)"
  - "tanhf (función)"
  - "tanf (función)"
  - "funciones trigonométricas"
  - "funciones hiperbólicas"
ms.assetid: 36cc0ce8-9c80-4653-b354-ddb3b378b6bd
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tan, tanf, tanl, tanh, tanhf, tanhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula la tangente \(`tan`, `tanf` o `tanl`\) o la tangente hiperbólica \(`tanh`, `tanhf` o `tanhl`\).  
  
## Sintaxis  
  
```  
double tan(  
   double x   
);  
float tan(  
   float x   
);  // C++ only  
long double tan(  
   long double x  
);  // C++ only  
float tanf(  
   float x   
);  
long double tanl(  
   long double x  
);  
double tanh(  
   double x   
);  
float tanh(  
   float x   
);  // C++ only  
long double tanh(  
   long double x  
);  // C++ only  
float tanhf(  
   float x   
);  
long double tanhl(  
   long double x  
);  
```  
  
#### Parámetros  
 `x`  
 Ángulo en radianes.  
  
## Valor devuelto  
 Las funciones de `tan` devuelven la tangente de `x`.  Si `x` es mayor o igual que 263, o menor o igual que –263, se produce una pérdida de significado en el resultado.  
  
 Las funciones de `tanh` devuelven la tangente hiperbólica de `x`.  No se devuelve ningún error.  
  
|Entrada|Excepción SEH|Excepción de `Matherr`|  
|-------------|-------------------|----------------------------|  
|± QNAN,IND|ninguno|\_DOMAIN|  
|± ∞  \(`tan`, `tanf`\)|`INVALID`|\_DOMAIN|  
  
## Comentarios  
 Dado que C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `tan` y `tanh` que toman y devuelven los valores `float` o `long double`.  En un programa de C, `tan` y `tanh` siempre toman y devuelven `double`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`tan`, `tanf`, `tanl`, `tanh`, `tanhf`, `tanhl`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_tan.c  
// This program displays the tangent of pi / 4  
// and the hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tan( pi / 4 );  
   y = tanh( x );  
   printf( "tan( %f ) = %f\n", pi/4, x );  
   printf( "tanh( %f ) = %f\n", x, y );  
}  
```  
  
  **tan\( 0,785398 \) \= 1,000000**  
**tanh\( 1,000000 \) \= 0,761594**   
## Equivalente en .NET Framework  
  
-   [System::Math::Tan](https://msdn.microsoft.com/en-us/library/system.math.tan.aspx)  
  
-   [System::Math::Tanh](https://msdn.microsoft.com/en-us/library/system.math.tanh.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Long double](../../misc/long-double.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [\_CItan](../../c-runtime-library/citan.md)