---
title: "sin, sinf, sinl, sinh, sinhf, sinhl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "sinl"
  - "sinf"
  - "sinhf"
  - "sinh"
  - "sin"
  - "sinhl"
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
  - "_sinl"
  - "sinf"
  - "sinhl"
  - "sinl"
  - "sin"
  - "sinhf"
  - "_sinhl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_sinhl (función)"
  - "_sinl (función)"
  - "calcular senos"
  - "funciones hiperbólicas"
  - "sin (función)"
  - "sinf (función)"
  - "sinh (función)"
  - "sinhf (función)"
  - "sinhl (función)"
  - "sinl (función)"
  - "funciones trigonométricas"
ms.assetid: 737de73e-3590-45f9-8257-dc1c0c489dfc
caps.latest.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 16
---
# sin, sinf, sinl, sinh, sinhf, sinhl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula senos y senos hiperbólicos.  
  
## Sintaxis  
  
```  
double sin(  
   double x   
);  
float sin(  
   float x  
);  // C++ only  
long double sin(  
   long double x  
);  // C++ only  
float sinf(  
   float x   
);  
long double sinl(  
   long double x  
);  
double sinh(  
   double x   
);  
float sinh(  
   float x   
);  // C++ only  
long double sinh(  
   long double x  
);  // C++ only  
float sinhf(  
   float x  
);  
long double sinhl(  
   long double x  
);  
```  
  
#### Parámetros  
 `x`  
 Ángulo en radianes.  
  
## Valor devuelto  
 Las funciones `sin` devuelven el seno de `x`.  Si `x` es mayor o igual que 263, o menor o igual que –263, se produce una pérdida de significado en el resultado.  
  
 Las funciones `sinh` devuelven seno hiperbólico de `x`.  De forma predeterminada, si el resultado es demasiado grande, `errno` establece `sinh` en `ERANGE` y devuelve ±`HUGE_VAL`.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-------------|-------------------|--------------------------|  
|± QNAN,IND|None|\_DOMAIN|  
|± ∞ \(sin, sinf, sinl\)|INVALID|\_DOMAIN|  
|&#124;x&#124; ≥ 7,104760e\+002 \(sinh, sinhf, sinhl\)|OVERFLOW\+INEXACT|OVERFLOW|  
  
 Para obtener más información sobre los códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Dado que C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `sin` y `sinh` que toman y devuelven los valores `float` o `long double`.  En un programa de C, `sin` y `sinh` siempre toman y devuelven `double`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`sin`, `sinf`, `sinl`, `sinh`, `sinhf`, `sinhl`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_sincos.c  
// This program displays the sine, hyperbolic  
// sine, cosine, and hyperbolic cosine of pi / 2.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = pi / 2;  
   y = sin( x );  
   printf( "sin( %f ) = %f\n", x, y );  
   y = sinh( x );  
   printf( "sinh( %f ) = %f\n",x, y );  
   y = cos( x );  
   printf( "cos( %f ) = %f\n", x, y );  
   y = cosh( x );  
   printf( "cosh( %f ) = %f\n",x, y );  
}  
```  
  
  **sin\(1,570796\) \= 1,000000**  
**sinh\(1,570796\) \= 2,301299**  
**cos\(1,570796\) \= 0,000000**  
**cosh\(1,570796\) \= 2,509178**   
## Equivalente en .NET Framework  
  
-   [System::Math::Sin](https://msdn.microsoft.com/en-us/library/system.math.sin.aspx)  
  
-   [System::Math::Sinh](https://msdn.microsoft.com/en-us/library/system.math.sinh.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CIsin](../../c-runtime-library/cisin.md)