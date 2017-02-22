---
title: "div | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "div"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "div"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "div (función)"
  - "dividir enteros"
  - "cocientes"
  - "cocientes, calcular"
  - "cálculo de restos"
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# div
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el cociente y el resto de dos valores enteros.  
  
## Sintaxis  
  
```  
div_t div(   
   int numer,  
   int denom   
);  
ldiv_t div(  
   long numer,  
   long denom  
); /* C++ only */   
lldiv_t div(  
   long long numer,  
   long long denom  
); /* C++ only */  
```  
  
#### Parámetros  
 `numer`  
 Numerador.  
  
 `denom`  
 Denominador.  
  
## Valor devuelto  
 El `div` al que se llama mediante argumentos de tipo `int` devuelve una estructura de tipo `div_t`, formada por el cociente y el resto.  El valor devuelto de la sobrecarga con argumentos de tipo `long` es `ldiv_t`.  `div_t` y `ldiv_t` se definen en STDLIB.H.  
  
## Comentarios  
 La función `div` divide `numer` por `denom` y, por tanto, calcula el cociente y el resto.  La estructura [div\_t](../../c-runtime-library/standard-types.md) contiene el cociente, `int` `quot`, y el resto, `int` `rem`.  El signo del cociente es el mismo que el del cociente matemático.  Su valor absoluto es el entero más grande que es menor que el valor absoluto del cociente matemático.  Si el denominador es 0, el programa se cierra con un mensaje de error.  
  
 Las sobrecargas que toman argumentos de tipo `long` o `long long` solo se pueden usar en código de C\+\+.  El tipo devuelto [ldiv\_t](../../c-runtime-library/standard-types.md) contiene los miembros `long` `quot` y `long` `rem`, y el tipo devuelto [lldiv\_t](../../c-runtime-library/standard-types.md) contiene los miembros `long long quot` y `long long rem`, que tienen los mismos significados que los miembros de `div_t`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`div`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_div.c  
// arguments: 876 13  
  
// This example takes two integers as command-line  
// arguments and displays the results of the integer  
// division. This program accepts two arguments on the  
// command line following the program name, then calls  
// div to divide the first argument by the second.  
// Finally, it prints the structure members quot and rem.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <math.h>  
  
int main( int argc, char *argv[] )  
{  
   int x,y;  
   div_t div_result;  
  
   x = atoi( argv[1] );  
   y = atoi( argv[2] );  
  
   printf( "x is %d, y is %d\n", x, y );  
   div_result = div( x, y );  
   printf( "The quotient is %d, and the remainder is %d\n",  
           div_result.quot, div_result.rem );  
}  
```  
  
  **x es 876, y es 13**  
**El cociente es 67 y el resto es 5**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ldiv, lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)