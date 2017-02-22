---
title: "ldexp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ldexp"
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
  - "ldexp"
  - "_ldexpl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "calcular números reales"
  - "cálculo de números reales"
  - "exponente, números de punto flotante"
  - "funciones de punto flotante, mantisa y exponente"
  - "ldexp (función)"
  - "mantisas, variables de punto flotante"
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# ldexp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Multiplica un número de punto flotante por una potencia integral de dos.  
  
## Sintaxis  
  
```  
double ldexp(    double x,    int exp  ); float ldexp(    float x,    int exp );  // C++ only long double ldexp(    long double x,    int exp );  // C++ only  float ldexpf(    float x,    int exp );  long double ldexpl(    long double x,    int exp );   
```  
  
#### Parámetros  
 `x`  
 Valor de punto flotante.  
  
 `exp`  
 Exponente de entero.  
  
## Valor devuelto  
 Si es correcta, la función `ldexp` devuelve el valor de `x` \* 2<sup>exp</sup>.  En caso de desbordamiento, y según cuál sea el signo de `x`, `ldexp` devuelve \+\/– `HUGE_VAL`; el valor de `errno` se establece en `ERANGE`.  
  
 Para más información sobre `errno` y otros posibles valores devueltos erróneos, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `ldexp` que toman los tipos `float` y `long double`.  En un programa C, `ldexp` siempre toma un `double` y un `int`, y devuelve un `double`.  
  
## Requisitos  
  
|Rutina|Encabezado C|Encabezado C\+\+|  
|------------|------------------|----------------------|  
|`ldexp`, `ldexpf`, `ldexpl`|\<math.h\>|\<cmath\>|  
  
 Para obtener información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_ldexp.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 4.0, y;  
   int p = 3;  
  
   y = ldexp( x, p );  
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );  
}  
```  
  
## Salida  
  
```  
4.0 times two to the power of 3 is 32.0  
```  
  
## Equivalente en .NET Framework  
 [System::Math::Pow](https://msdn.microsoft.com/en-us/library/system.math.pow.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [modf, modff, modfl](../../c-runtime-library/reference/modf-modff-modfl.md)