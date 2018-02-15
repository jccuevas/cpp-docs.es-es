---
title: modf, modff, modfl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
dev_langs:
- C++
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9744b82cd14d29234fabf1edbe379c2c5d14ac85
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl
Divide un valor de punto flotante en partes fraccionarias y enteras.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double modf(  
   double x,  
   double * intptr   
);  
float modf(  
   float x,  
   float * intptr  
);  // C++ only  
long double modf(  
   long double x,  
   long double * intptr  
);  // C++ only  
float modff(  
   float x,  
   float * intptr   
);  
long double modfl(  
   long double x,  
   long double * intptr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *x*  
 Valor de punto flotante.  
  
 `intptr`  
 Puntero a la parte entera almacenada.  
  
## <a name="return-value"></a>Valor devuelto  
 Esta función devuelve la parte fraccionaria con signo de *x*. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 Las funciones `modf` desglosan el valor de punto flotante `x` en fracciones y partes de enteros, cada uno de los cuales tiene el mismo signo que `x`. Se devuelve la parte fraccionaria con signo de `x`. La parte entera se almacena como un valor de punto flotante en `intptr.`  
  
 `modf` tiene una implementación que usa las Extensiones SIMD de transmisión por secuencias 2 (SSE2). Consulte [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md) para obtener información y conocer las restricciones sobre el uso de la implementación de SSE2.  
  
 Puesto que C++ permite las sobrecargas, es posible llamar a las sobrecargas de `modf` que toman y devuelven los parámetros `float` o `long double`. En un programa de C, `modf` siempre toma dos valores double y devuelve uno.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`modf`, `modff`, `modfl`|C: \<math.h><br /><br /> C++: \<cmath> o \<math.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="libraries"></a>Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_modf.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y, n;  
  
   x = -14.87654321;      /* Divide x into its fractional */  
   y = modf( x, &n );     /* and integer parts            */  
  
   printf( "For %f, the fraction is %f and the integer is %.f\n",   
           x, y, n );  
}  
```  
  
## <a name="output"></a>Salida  
  
```  
For -14.876543, the fraction is -0.876543 and the integer is -14  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)