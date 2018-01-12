---
title: ldexp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: ldexp
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
- ldexp
- _ldexpl
dev_langs: C++
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a5e38d9a8df63fd4c2880fda7becec545c9584a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ldexp"></a>ldexp
Multiplica un número de punto flotante por una potencia integral de dos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double ldexp(  
   double x,  
   int exp   
);  
float ldexp(  
   float x,  
   int exp  
);  // C++ only  
long double ldexp(  
   long double x,  
   int exp  
);  // C++ only   
float ldexpf(  
   float x,  
   int exp  
);   
long double ldexpl(  
   long double x,  
   int exp  
);   
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante.  
  
 `exp`  
 Exponente de entero.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcta, la función `ldexp` devuelve el valor de `x` * 2<sup>exp</sup>. Si se produce desbordamiento y según cuál sea el signo de `x`, `ldexp` devuelve `HUGE_VAL`; el `errno` valor se establece en `ERANGE`.  
  
 Para obtener más información sobre `errno` y los posibles valores de error devueltos, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 Como C++ permite las sobrecargas, puede llamar a las sobrecargas de `ldexp` que toman los tipos `float` y `long double`. En un programa C, `ldexp` siempre toma un `double` y un `int`, y devuelve un `double`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado C|Encabezado C++|  
|-------------|--------------|------------------|  
|`ldexp`, `ldexpf`, `ldexpl`|\<math.h>|\<cmath>|  
  
 Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="output"></a>Salida  
  
```  
4.0 times two to the power of 3 is 32.0  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [modf, modff, modfl](../../c-runtime-library/reference/modf-modff-modfl.md)