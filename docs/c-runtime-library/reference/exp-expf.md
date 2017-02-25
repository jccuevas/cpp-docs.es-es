---
title: "exp, expf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "expf"
  - "exp"
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
  - "_expl"
  - "expf"
  - "exp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cálculos exponenciales"
  - "expf (función)"
  - "calcular exponenciales"
  - "exp (función)"
ms.assetid: 7070016d-1143-407e-9e9a-6b059bb88867
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# exp, expf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el exponencial.  
  
## Sintaxis  
  
```  
double exp(   
   double x  
);  
float exp(  
   float x  
);  // C++ only  
long double exp(  
   long double x  
);  // C++ only  
float expf(   
   float x  
);  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
## Valor devuelto  
 La función de `exp` devuelve el valor exponencial del parámetro flotante, `x`, si correctamente.  Es decir, el resultado es e a la potencia `x`, donde es la base e del logaritmo natural.  En desbordamiento, la función devuelve los INF \(infinitos\) y en subdesbordamiento, `exp` devuelve 0.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-------------|-------------------|--------------------------|  
|± QNAN,IND|None|\_DOMAIN|  
|± ∞|INVALID|\_DOMAIN|  
|x ≥ 7.097827e\+002|INEXACT\+OVERFLOW|OVERFLOW|  
|X ≤ \-7.083964e\+002|INEXACT\+UNDERFLOW|SUBDESBORDAMIENTO|  
  
 `exp` tiene una implementación que usa las Extensiones SIMD de transmisión por secuencias 2 \(SSE2\).  Vea [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md) para la información y las restricciones de utilizar la implementación SSE2.  
  
## Comentarios  
 C\+\+ permite la sobrecarga, por lo que puede llamar a sobrecargas de `exp`.  En un programa de C, `exp` siempre toma y devuelve un tipo double.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`exp`, `expf`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_exp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.302585093, y;  
  
   y = exp( x );  
   printf( "exp( %f ) = %f\n", x, y );  
}  
```  
  
  **exp \(2,302585\) \= 10,000000**   
## Equivalente en .NET Framework  
 [System::Math::Exp](https://msdn.microsoft.com/en-us/library/system.math.exp.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [\_CIexp](../../c-runtime-library/ciexp.md)