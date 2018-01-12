---
title: log, logf, log10, log10f | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- log10f
- logf
- log10
- log
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- logf
- _log10l
- log
- _logl
- log10f
- log10
dev_langs: C++
helpviewer_keywords:
- calculating logarithms
- log10f function
- log10 function
- log function
- logf function
- logarithms
ms.assetid: 7adc77c2-04f7-4245-a980-21215563cfae
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d60347bc47c05a19cb1487e7a6738d328c78f846
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="log-logf-log10-log10f"></a>log, logf, log10, log10f
Calcula logaritmos.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 *x*  
 Valor cuyo logaritmo hay que calcular.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, las funciones **log** devuelven el logaritmo natural (base e) de *x*. Las funciones log10 devuelven el logaritmo en base 10. Si *x* es negativo, estas funciones devuelven un valor indefinido de forma predeterminada. Si *x* es 0, devuelven INF (infinito).  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-----------|-------------------|-----------------------|  
|± QNAN,IND|ninguna|_DOMAIN|  
|± 0|ZERODIVIDE|_SING|  
|x < 0|INVALID|_DOMAIN|  
  
 **log** y `log10` tienen una implementación que usa las extensiones SIMD de transmisión por secuencias 2 (SSE2). Vea [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md) para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2.  
  
## <a name="remarks"></a>Comentarios  
 C++ permite las sobrecargas, así que puede llamar a las sobrecargas de **log** y `log10`. En un programa de C, **log** y `log10` siempre toman y devuelven un valor doble.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|**log**, `logf`, `log10`, `log10f`|\<math.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="output"></a>Salida  
  
```  
log( 9000.00 ) = 9.104980  
log10( 9000.00 ) = 3.954243  
```  
  
 Para generar los logaritmos para otras bases, use la siguiente relación matemática: logaritmo base b de a == logaritmo natural (a) / logaritmo natural (b).  
  
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
  
## <a name="output"></a>Salida  
  
```  
Log base 2 of 65536.000000 is 16.000000  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [EXP, expf, expl](../../c-runtime-library/reference/exp-expf.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [pow, powf, powl](../../c-runtime-library/reference/pow-powf-powl.md)   
 [_CIlog](../../c-runtime-library/cilog.md)   
 [_CIlog10](../../c-runtime-library/cilog10.md)