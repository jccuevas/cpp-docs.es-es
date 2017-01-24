---
title: "fmod, fmodf | Microsoft Docs"
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
  - "fmod"
  - "fmodf"
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
  - "fmod"
  - "_fmodl"
  - "fmodf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "calcular restos de punto flotante"
  - "fmodf (función)"
  - "fmod (función)"
  - "números de punto flotante, calcular restos"
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fmod, fmodf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el resto flotante.  
  
## Sintaxis  
  
```  
double fmod(   
   double x,  
   double y   
);  
float fmod(  
   float x,  
   float y   
);  // C++ only  
long double fmod(  
   long double x,  
   long double y  
);  // C++ only  
float fmodf(   
   float x,  
   float y   
);  
```  
  
#### Parámetros  
 `x`, `y`  
 Valores de punto flotante.  
  
## Valor devuelto  
 `fmod` devuelve el resto de punto flotante de `x` \/ `y`.  Si el valor de `y` es 0,0, `fmod` devuelve un valor NaN reservado.  Para obtener información sobre la representación de un NaN reserva de la familia de `printf` , vea [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## Comentarios  
 La función `fmod` calcula el resto del punto flotante `f` de `x` \/ `y` de manera que `x` \= `i` `*` `y` \+ `f`, donde `i` es un entero, `f` tiene el mismo signo que `x` y el valor absoluto de `f` es menor que el valor absoluto de `y`.  
  
 C\+\+ permite la sobrecarga, por lo que puede llamar a sobrecargas de `fmod`.  En un programa C, `fmod` siempre toma dos valores Double y devuelve uno.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`fmod`, `fmodf`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fmod.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = fmod( w, x );  
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );  
}  
```  
  
  **El resto de \-10,00\/3,00 es \-1,000000**   
## Equivalente en .NET Framework  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ceil, ceilf, ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [fabs, fabsf, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [floor, floorf, floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [\_CIfmod](../../c-runtime-library/cifmod.md)