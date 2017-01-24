---
title: "sqrt, sqrtf, sqrtl | Microsoft Docs"
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
  - "sqrtl"
  - "sqrtf"
  - "sqrt"
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
  - "sqrt"
  - "sqrtf"
  - "_sqrtl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sqrtl (función)"
  - "calcular raíces cuadradas"
  - "sqrt (función)"
  - "sqrtf (función)"
  - "sqrtl (función)"
  - "raíces cuadradas, calcular"
ms.assetid: 2ba9467b-f172-41dc-8f10-b86f68fa813c
caps.latest.revision: 18
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sqrt, sqrtf, sqrtl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula la raíz cuadrada.  
  
## Sintaxis  
  
```  
double sqrt(    double x  ); float sqrt(    float x  );  // C++ only long double sqrt(    long double x );  // C++ only float sqrtf(    float x  ); long double sqrtl(    long double x  );  
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante no negativo  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `sqrt` que toman los tipos `float` y `long double`.  En un programa C, `sqrt` siempre toma y devuelve un tipo `double`.  
  
## Valor devuelto  
 Las funciones `sqrt` devuelven la raíz cuadrada de `x`.  Si `x` es negativo, `sqrt` devuelve un NaN indefinido de forma predeterminada.  
  
|Entrada|Excepción SEH|Excepción de `_matherr`|  
|-------------|-------------------|-----------------------------|  
|± QNAN,IND|ninguna|\_DOMAIN|  
|\- ∞|ninguna|\_DOMAIN|  
|x\<0|ninguna|\_DOMAIN|  
  
## Requisitos  
  
|Función|Encabezado C|Encabezado C\+\+|  
|-------------|------------------|----------------------|  
|`sqrt`, `sqrtf`, `sqrtl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_sqrt.c  
// This program calculates a square root.  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   double question = 45.35, answer;  
   answer = sqrt( question );  
   if( question < 0 )  
      printf( "Error: sqrt returns %f\n", answer );  
   else  
      printf( "The square root of %.2f is %.2f\n", question, answer );  
}  
```  
  
  **La raíz cuadrada de 45,35 es 6,73**   
## Equivalente en .NET Framework  
 [System::Math::Sqrt](https://msdn.microsoft.com/en-us/library/system.math.sqrt.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [exp, expf](../../c-runtime-library/reference/exp-expf.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [pow, powf, powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [\_CIsqrt](../../c-runtime-library/cisqrt.md)