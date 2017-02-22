---
title: "imaxdiv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "imaxdiv"
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
  - "imaxdiv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "imaxdiv (función)"
ms.assetid: 7d90126f-fdc2-4986-9cdf-94e4c9123d26
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# imaxdiv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el cociente y el resto de dos valores enteros de cualquier tamaño como una sola operación.  
  
## Sintaxis  
  
```  
imaxdiv_t imaxdiv(   
   intmax_t numer,  
   intmax_t denom   
);   
```  
  
#### Parámetros  
 `numer`  
 Numerador.  
  
 `denom`  
 Denominador.  
  
## Valor devuelto  
 `imaxdiv` llamado con argumentos del tipo [intmax\_t](../../c-runtime-library/standard-types.md) devuelve una estructura del tipo [imaxdiv\_t](../../c-runtime-library/standard-types.md) que compone el cociente y el resto.  
  
## Comentarios  
 La función `imaxdiv` divide `numer` por `denom` y, por tanto, calcula el cociente y el resto.  La estructura `imaxdiv_t` contiene el cociente, `intmax_t` `quot`, y el resto, `intmax_t` `rem`.  El signo del cociente es el mismo que el del cociente matemático.  Su valor absoluto es el entero más grande que es menor que el valor absoluto del cociente matemático.  Si el denominador es 0, el programa se cierra con un mensaje de error.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`imaxdiv`|\<inttypes.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_imaxdiv.c  
// Build using: cl /W3 /Tc crt_imaxdiv.c  
// This example takes two integers as command-line  
// arguments and calls imaxdiv to divide the first   
// argument by the second, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x,y;  
   imaxdiv_t div_result;  
  
   x = atoll(argv[1]);  
   y = atoll(argv[2]);  
  
   printf("The call to imaxdiv(%lld, %lld)\n", x, y);  
   div_result = imaxdiv(x, y);  
   printf("results in a quotient of %lld, and a remainder of %lld\n\n",  
          div_result.quot, div_result.rem);  
}  
```  
  
 Cuando se compila y se llama con los parámetros de la línea de comandos `9460730470000000 8766`, el código genera esta salida:  
  
  **La llamada a imaxdiv\(9460730470000000, 8766\)**  
**resulta en un cociente de 1079252848505 y un resto de 5170**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [ldiv, lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)