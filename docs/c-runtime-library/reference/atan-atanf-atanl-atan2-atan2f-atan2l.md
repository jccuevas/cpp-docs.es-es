---
title: "atan, atanf, atanl, atan2, atan2f, atan2l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "atan2f"
  - "atan2l"
  - "atan2"
  - "atanf"
  - "atan"
  - "atanl"
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
  - "atan"
  - "atan2l"
  - "atan2"
  - "atanl"
  - "atanf"
  - "atan2f"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "arctangent (función)"
  - "atan (función)"
  - "atan2 (función)"
  - "atan2f (función)"
  - "atan2l (función)"
  - "atanf (función)"
  - "atanl (función)"
  - "funciones trigonométricas"
ms.assetid: 7a87a18e-c94d-4727-9cb1-1bb5c2725ae4
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# atan, atanf, atanl, atan2, atan2f, atan2l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el arco tangente de `x` \(`atan`, `atanf` y `atanl`\), o el arco tangente de `y`\/`x` \(`atan2`, `atan2f` y `atan2l`\).  
  
## Sintaxis  
  
```  
double atan(   
   double x   
);  
float atan(  
   float x   
);  // C++ only  
long double atan(  
   long double x  
);  // C++ only  
double atan2(   
   double y,   
   double x   
);  
float atan2(  
   float y,  
   float x  
);  // C++ only  
long double atan2(  
   long double y,  
   long double x  
);  // C++ only  
float atanf(   
   float x   
);  
long double atanl(  
   long double x  
);  
float atan2f(  
   float y,  
   float x  
);  
long double atan2l(  
   long double y,  
   long double x  
);  
```  
  
#### Parámetros  
 `x`, `y`  
 Cualquier número.  
  
## Valor devuelto  
 `atan` devuelve el arco tangente de `x` en el intervalo comprendido entre –π\/2 y π\/2 radianes.  `atan2` devuelve el arco tangente de `y/x` en el intervalo comprendido entre –π y π radianes.  Si `x` es 0, `atan` devuelve 0.  Si los dos parámetros de `atan2` son 0, la función devuelve 0.  Todos los resultados están en radianes.  
  
 `atan2` utiliza los signos de los dos parámetros para determinar el cuadrante del valor devuelto.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-------------|-------------------|--------------------------|  
|± `QNAN`,`IND`|ninguno|`_DOMAIN`|  
  
## Comentarios  
 La función `atan` calcula el arco tangente \(función tangente inversa\) de `x`.  `atan2` calcula el arco tangente de `y`\/`x` \(si `x` es igual a 0, `atan2` devuelve π\/2 si `y` es positivo, devuelve \- π\/2 si `y` es negativo, y devuelve 0 si `y` es 0\).  
  
 `atan` tiene una implementación que usa las Extensiones SIMD de transmisión por secuencias 2 \(SSE2\).  Para obtener información y las restricciones sobre el uso de la implementación de SSE2, vea [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md).  
  
 Dado que C\+\+ admite sobrecargas, puede llamar a sobrecargas de `atan` y `atan2`.  En un programa de C, `atan` y `atan2` siempre toman y devuelven valores double.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`atan`, `atan2`, `atanf`, `atan2f`, `atanl`, `atan2l`|\<math.h\>|  
  
## Ejemplo  
  
```  
// crt_atan.c  
// arguments: 5 0.5  
#include <math.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )   
{  
   double x, y, theta;  
   if( ac != 3 ){  
      fprintf( stderr, "Usage: %s <x> <y>\n", av[0] );  
      return 1;  
   }  
   x = atof( av[1] );  
   theta = atan( x );  
   printf( "Arctangent of %f: %f\n", x, theta );  
   y = atof( av[2] );  
   theta = atan2( y, x );  
   printf( "Arctangent of %f / %f: %f\n", y, x, theta );   
   return 0;  
}  
```  
  
  **Arco tangente de 5,000000: 1,373401**  
**Arco tangente de 0,500000 \/ 5,000000: 0,099669**   
## Equivalente en .NET Framework  
  
-   [System::Math::Atan](https://msdn.microsoft.com/en-us/library/system.math.atan.aspx)  
  
-   [System::Math::Atan2](https://msdn.microsoft.com/en-us/library/system.math.atan2.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [\_CIatan](../../c-runtime-library/ciatan.md)   
 [\_CIatan2](../../c-runtime-library/ciatan2.md)