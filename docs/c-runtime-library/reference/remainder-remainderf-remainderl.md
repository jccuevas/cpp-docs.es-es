---
title: "remainder, remainderf, remainderl | Microsoft Docs"
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
  - "remainderl"
  - "remainder"
  - "remainderf"
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
  - "remainderf"
  - "remainder"
  - "remainderl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "remainderf"
  - "remainderl"
  - "remainder"
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# remainder, remainderf, remainderl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el resto del cociente de dos valores de punto flotante, redondeado al valor entero más cercano.  
  
## Sintaxis  
  
```  
double remainder(   
   double numer,  
   double denom  
);  
float remainder(   
   float numer,  
   float denom  
); /* C++ only */  
long double remainder(   
   long double numer,  
   long double denom  
); /* C++ only */  
float remainderf(   
   float numer,  
   float denom  
);  
long double remainderl(   
   long double numer,  
   long double denom  
);  
  
```  
  
#### Parámetros  
 `numer`  
 Numerador.  
  
 `denom`  
 Denominador.  
  
## Valor devuelto  
 El resto de punto flotante de `x` \/ `y`.  Si el valor de `y` es 0,0, `remainder` devuelve un valor NaN reservado.  Para obtener información sobre la representación de un valor NaN reservado por la familia `printf`, vea [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## Comentarios  
 La función de `remainder` calcula el resto flotante `r` de `x`\/`y` tales que `x` \= `n` \* `y` \+ `r`, donde es el entero `n` más cercana en valor a `x`\/`y` y `n` incluso es siempre que &#124; `n` \- `x` \/ `y` &#124; \= 1\/2.  Cuando `r` \= 0, `r` tiene el mismo signo que `x`.  
  
 Puesto que C\+\+ permite las sobrecargas, es posible llamar a las sobrecargas de `remainder` que toman y devuelven los valores `float` o `long double`.  En un programa C, `remainder` siempre toma dos valores Double y devuelve uno.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`remainder`, `remainderf`, `remainderl`|\<math.h\>|  
  
 Para obtener información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```c  
// crt_remainder.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
  
   z = remainder(w, x);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
}  
```  
  
  **El resto de \-10,00\/3,00 es \-1,000000**   
## Equivalente en .NET Framework  
 [System::Math::IEEERemainder](https://msdn.microsoft.com/en-us/library/system.math.ieeeremainder.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ldiv, lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remquo, remquof, remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)