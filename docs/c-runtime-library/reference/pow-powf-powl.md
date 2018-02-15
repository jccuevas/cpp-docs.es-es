---
title: pow, powf, powl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
dev_langs:
- C++
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 09b618e557fffadd3bfffb431fc7e89458c4f420
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="pow-powf-powl"></a>pow, powf, powl
Calcula el valor de `x` elevado a la potencia de `y`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double pow(  
   double x,  
   double y   
);  
double pow(  
   double x,  
   int y  
);  // C++ only  
float pow(  
   float x,  
   float y   
);  // C++ only  
float pow(  
   float x,  
   int y  
);  // C++ only  
long double pow(  
   long double x,  
   long double y  
);  // C++ only  
long double pow(  
   long double x,  
   int y  
);  // C++ only  
float powf(  
   float x,  
   float y   
);  
long double powl(  
   long double x,  
   long double y  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Base.  
  
 `y`  
 Exponente.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el valor de `x`<sup>y</sup>. No se imprime ningún mensaje de error en caso de desbordamiento o subdesbordamiento.  
  
|Valores de x e y|Valor devuelto de pow|  
|-----------------------|-------------------------|  
|`x` \< > 0 y `y` = 0.0|1|  
|`x` = 0,0 e `y` = 0,0|1|  
|`x` = 0,0 e `y` < 0|INF|  
  
## <a name="remarks"></a>Comentarios  
 `pow` no reconoce los valores de punto flotante enteros mayores que 2<sup>64`1.0E100` (por ejemplo, </sup>).  
  
 `pow` tiene una implementación que usa las Extensiones SIMD de transmisión por secuencias 2 (SSE2). Para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2, vea [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md).  
  
 Como C++ admite sobrecargas, se puede llamar a cualquiera de las sobrecargas de `pow`. En un programa de C, `pow` siempre toma dos valores double y devuelve uno.  
  
 La sobrecarga de `pow(int, int)` ya no está disponible. Si usa esta sobrecarga, el compilador puede emitir C2668. Para evitar este problema, convierta el primer parámetro en `double`, `float` o `long double`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`pow`, `powf`, `powl`|\<math.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_pow.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x = 2.0, y = 3.0, z;  
  
   z = pow( x, y );  
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
2.0 to the power of 3.0 is 8.0  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [exp, expf, expl](../../c-runtime-library/reference/exp-expf.md)   
 [log, logf, log10, log10f](../../c-runtime-library/reference/log-logf-log10-log10f.md)   
 [sqrt, sqrtf, sqrtl](../../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)   
 [_CIpow](../../c-runtime-library/cipow.md)