---
title: "frexp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "frexp"
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
  - "frexp"
  - "_frexpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_frexpl (función)"
  - "exponente, números de punto flotante"
  - "funciones de punto flotante, mantisa y exponente"
  - "frexp (función)"
  - "frexpl (función)"
  - "mantisas, variables de punto flotante"
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# frexp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la mantisa y el exponente de un número de punto flotante.  
  
## Sintaxis  
  
```  
double frexp(  
   double x,  
   int *expptr   
);  
float frexp(  
   float x,  
   int * expptr  
);  // C++ only  
long double frexp(  
   long double x,  
   int * expptr  
);  // C++ only  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
 `expptr`  
 Puntero al exponente entero almacenado.  
  
## Valor devuelto  
 `frexp` devuelve la mantisa.  Si `x` es 0, la función devuelve 0 para la mantisa y el exponente.  Si `expptr` es `NULL`, se invoca el controlador no válido del parámetro tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, conjuntos `errno` de esta función a `EINVAL` y devuelven 0.  
  
## Comentarios  
 La función de `frexp` analiza el valor de punto flotante \(`x`\) en una mantisa \(`m`\) y un exponente \(`n`\), de forma que el valor absoluto de `m` es mayor o igual que 0,5 y menor que 1,0, y `x` \= `m`\*2.<sup>n</sup> Almacenan el exponente entero `n` en la ubicación a la que `expptr`.  
  
 C\+\+ permite la sobrecarga, por lo que puede llamar a sobrecargas de `frexp`.  En un programa de c., `frexp` toma un doble y un entero y devuelve siempre un doble.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`frexp`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_frexp.c  
// This program calculates frexp( 16.4, &n )  
// then displays y and n.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y;  
   int n;  
  
   x = 16.4;  
   y = frexp( x, &n );  
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );  
}  
```  
  
  **frexp \(16,400000, &n\) \= 0,512500, n \= 5**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)   
 [modf, modff, modfl](../../c-runtime-library/reference/modf-modff-modfl.md)