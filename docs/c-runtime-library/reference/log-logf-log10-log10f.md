---
title: "log, logf, log10, log10f | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "log10f"
  - "logf"
  - "log10"
  - "log"
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
  - "logf"
  - "_log10l"
  - "log"
  - "_logl"
  - "log10f"
  - "log10"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "calcular logaritmos"
  - "log10f (función)"
  - "log10 (función)"
  - "log (función)"
  - "logf (función)"
  - "logaritmos"
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# log, logf, log10, log10f
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula los logaritmos.  
  
## Sintaxis  
  
```  
  
      double log(  
   double x   
);  
float log(  
   float x  
);  // C++ only  
long double log(  
   long double x  
);  // C++ only  
float logf(  
   float x   
);  
double log10(  
   double x  
);  
float log10(  
   float x  
);  // C++ only  
long double log10(  
   long double x  
);  // C++ only  
float log10f (  
   float x  
);  
```  
  
#### Parámetros  
 *x*  
 Valor cuyo logaritmo debe encontrar.  
  
## Valor devuelto  
 Las funciones de **log** devuelve el logaritmo natural \(base e\) *de x* si correctamente.  Las funciones log10 devuelve el logaritmo base\-10.  Si *x* es negativo, estas funciones devuelven un definido, de forma predeterminada.  Si *x* es 0, devuelve los INF \(infinitos\).  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-------------|-------------------|--------------------------|  
|± QNAN,IND|ninguno|\_DOMAIN|  
|± 0|ZERODIVIDE|\_SING|  
|x \< 0|INVALID|\_DOMAIN|  
  
 **log** y `log10` tiene una implementación que utilice las extensiones 2 \(SSE2\) de Streaming SIMD.  Vea [\_set\_SSE2\_enable](../../c-runtime-library/reference/set-sse2-enable.md) para la información y las restricciones de utilizar la implementación SSE2.  
  
## Comentarios  
 C\+\+ permite la sobrecarga, por lo que puede llamar a sobrecargas de **log** y de `log10`.  En un programa de c., **log** y `log10` toman y devuelven siempre un doble.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**log**, `logf`, `log10`, `log10f`|\<math.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_log.c  
/* This program uses log and log10  
 * to calculate the natural logarithm and  
 * the base-10 logarithm of 9,000.  
 */  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 9000.0;  
   double y;  
  
   y = log( x );  
   printf( "log( %.2f ) = %f\n", x, y );  
   y = log10( x );  
   printf( "log10( %.2f ) = %f\n", x, y );  
}  
```  
  
## Resultados  
  
```  
log( 9000.00 ) = 9.104980  
log10( 9000.00 ) = 3.954243  
```  
  
 Para generar los logaritmos para otras bases, utilice la relación matemática: registrar b base de un logaritmo natural \=\= \(a\)\/logaritmo natural \(b\).  
  
```  
// logbase.cpp  
#include <math.h>  
#include <stdio.h>  
  
double logbase(double a, double base)  
{  
   return log(a) / log(base);  
}  
  
int main()  
{  
   double x = 65536;  
   double result;  
  
   result = logbase(x, 2);  
   printf("Log base 2 of %lf is %lf\n", x, result);  
}  
```  
  
## Resultados  
  
```  
Log base 2 of 65536.000000 is 16.000000  
```  
  
## Equivalente en .NET Framework  
  
-   [System::Math::Log](https://msdn.microsoft.com/en-us/library/system.math.log.aspx)  
  
-   [System::Math::Log10](https://msdn.microsoft.com/en-us/library/system.math.log10.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [exp, expf](../../c-runtime-library/reference/exp-expf.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [pow, powf, powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [\_CIlog](../../c-runtime-library/cilog.md)   
 [\_CIlog10](../../c-runtime-library/cilog10.md)