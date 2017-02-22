---
title: "ldiv, lldiv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ldiv"
  - "lldiv"
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
  - "ldiv"
  - "lldiv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "calcular cocientes"
  - "calcular restos"
  - "ldiv (función)"
  - "lldiv (función)"
  - "cocientes, calcular"
  - "cálculo de restos"
ms.assetid: 68ab5d83-27a4-479c-9d52-d055eb139eca
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# ldiv, lldiv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el cociente y el resto de dos enteros como una operación.  
  
## Sintaxis  
  
```  
ldiv_t ldiv(  
   long numer,  
   long denom   
);  
lldiv_t lldiv(  
   long long numer,  
   long long denom   
);  
```  
  
#### Parámetros  
 `numer`  
 Numerador.  
  
 `denom`  
 Denominador.  
  
## Valor devuelto  
 `ldiv` devuelve una estructura de tipo [ldiv\_t](../../c-runtime-library/standard-types.md) formada por el cociente y el resto.  `lldiv` devuelve una estructura de tipo [lldiv\_t](../../c-runtime-library/standard-types.md) formada por el cociente y el resto.  
  
## Comentarios  
 Las funciones `ldiv` y `lldiv` dividen `numer` por `denom` y, por tanto, calculan el cociente y el resto.  El signo del cociente es el mismo que el del cociente matemático.  El valor absoluto del cociente es el entero más grande que es menor que el valor absoluto del cociente matemático.  Si el denominador es 0, el programa se cierra con un mensaje de error.  `ldiv` y `lldiv` son iguales que `div`, salvo que los argumentos de `ldiv` y los miembros de la estructura devuelta son todos del tipo `long`, y los argumentos de `lldiv` y los miembros de la estructura devuelta son del tipo `long long`.  
  
 Las estructuras de `ldiv_t` y `lldiv_t` se definen en \<stdlib.h.\>.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`ldiv`, `lldiv`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_ldiv.c  
  
#include <stdlib.h>  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   long x = 5149627, y = 234879;  
   ldiv_t div_result;  
  
   div_result = ldiv( x, y );  
   printf( "For %ld / %ld, the quotient is ", x, y );  
   printf( "%ld, and the remainder is %ld\n",   
            div_result.quot, div_result.rem );  
}  
```  
  
## Resultados  
  
```  
For 5149627 / 234879, the quotient is 21, and the remainder is 217168  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [div](../../c-runtime-library/reference/div.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)