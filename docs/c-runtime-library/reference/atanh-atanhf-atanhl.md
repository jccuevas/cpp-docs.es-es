---
title: atanh, atanhf, atanhl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- atanhl
- atanhf
- atanh
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
- atanhl
- atanhf
- atanh
dev_langs:
- C++
helpviewer_keywords:
- atanhf function
- atanhl function
- atanh funciton
ms.assetid: 83a43b5b-2580-4461-854f-dc84236d9f32
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 4648fb28d20951b045abde39d0238de81a133f0c
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="atanh-atanhf-atanhl"></a>atanh, atanhf, atanhl
Calcula la tangente hiperbólica inversa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double atanh(  
   double x   
);  
float atanh(  
   float x   
);  // C++ only  
long double atanh(  
   long double x  
);  // C++ only  
float atanhf(  
   float x   
);  
long double atanhl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante.  
  
## <a name="return-value"></a>Valor devuelto  
 Las funciones `atanh` devuelven la tangente hiperbólica inversa (arcotangente hiperbólica) de `x`. Si `x` es mayor que 1 o menor que -1, `errno` está establecido en `EDOM` y el resultado es un valor NaN reservado. Si `x` equivale a 1 o -1, se devuelve un valor infinito positivo o negativo respectivamente, y `errno` se establece en `ERANGE`.  
  
|Entrada|Excepción SEH|Excepción de `Matherr`|  
|-----------|-------------------|-------------------------|  
|± QNAN,IND|ninguna|ninguna|  
|`X` ≥ 1; `x` ≤ -1|ninguna|ninguna|  
  
## <a name="remarks"></a>Comentarios  
 Puesto que C++ permite las sobrecargas, es posible llamar a las sobrecargas de `atanh` que toman y devuelven los valores `float` o `long double`. En un programa C, `atanh` siempre toma y devuelve un tipo `double`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`atanh`, `atanhf`, `atanhl`|\<math.h>|\<cmath>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_atanh.c  
// This program displays the hyperbolic tangent of pi / 4  
// and the arc hyperbolic tangent of the result.  
//  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double pi = 3.1415926535;  
   double x, y;  
  
   x = tanh( pi / 4 );  
   y = atanh( x );  
   printf( "tanh( %f ) = %f\n", pi/4, x );  
   printf( "atanh( %f ) = %f\n", x, y );  
}  
```  
  
```Output  
tanh( 0.785398 ) = 0.655794  
atanh( 0.655794 ) = 0.785398  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_CItan](../../c-runtime-library/citan.md)
