---
title: "modf, modff, modfl | Microsoft Docs"
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
  - "modff"
  - "modf"
  - "modfl"
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
  - "modff"
  - "_modfl"
  - "modf"
  - "modfl"
  - "math/modf"
  - "math/modff"
  - "math/modfl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "modf (función)"
  - "modff (función)"
  - "modfl (función)"
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# modf, modff, modfl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Divide un valor de punto flotante en fracciones y partes enteras.  
  
## Sintaxis  
  
```  
double modf(  
   double x,  
   double * intptr   
);  
float modf(  
   float x,  
   float * intptr  
);  // C++ only  
long double modf(  
   long double x,  
   long double * intptr  
);  // C++ only  
float modff(  
   float x,  
   float * intptr   
);  
long double modfl(  
   long double x,  
   long double * intptr  
);  
```  
  
#### Parámetros  
 *x*  
 Valor de punto flotante.  
  
 `intptr`  
 Puntero a la parte entera almacenado.  
  
## Valor devuelto  
 Esta función devuelve la parte fraccionaria firmada del *x*. No se devuelve ningún error.  
  
## Comentarios  
 El `modf` funciones desglosar el valor de punto flotante `x` en fracciones y partes de enteros, cada uno de los cuales tiene el mismo signo que `x`. La parte fraccionaria firmada de `x` se devuelve. La parte entera se almacena como un valor de punto flotante en `intptr.`  
  
 `modf` tiene una implementación que usa las Extensiones SIMD de transmisión por secuencias 2 \(SSE2\). Consulte [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md) para obtener información y restricciones en el uso de la implementación de SSE2.  
  
 C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `modf` que toman y devuelven `float` o `long double` parámetros. En un programa de C, `modf` siempre toma dos valores double y devuelve uno.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`modf`, `modff`, `modfl`|C: \< math.h \><br /><br /> C\+\+:, \< cmath \> o \< math.h \>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_modf.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y, n;  
  
   x = -14.87654321;      /* Divide x into its fractional */  
   y = modf( x, &n );     /* and integer parts            */  
  
   printf( "For %f, the fraction is %f and the integer is %.f\n",   
           x, y, n );  
}  
```  
  
## Salida  
  
```  
For -14.876543, the fraction is -0.876543 and the integer is -14  
```  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)