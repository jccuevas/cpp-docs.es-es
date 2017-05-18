---
title: cos, cosf, cosl, cosh, coshf, coshl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- coshl
- cosh
- cos
- cosl
- cosf
- coshf
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
- coshl
- cos
- cosf
- cosh
- cosl
- coshf
dev_langs:
- C++
helpviewer_keywords:
- cosines
- cosl function
- calculating cosine
- cosf function
- cos function
- cosh function
- coshf function
- trigonometric functions
- cosines, calculating
- coshl function
- hyperbolic functions
ms.assetid: ae90435e-6b68-4a47-a81f-be87d5c08f16
caps.latest.revision: 17
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
ms.openlocfilehash: f1fb949ba33299a8d18c41341b5fd76a776ee387
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="cos-cosf-cosl-cosh-coshf-coshl"></a>cos, cosf, cosl, cosh, coshf, coshl
Calcula el coseno (`cos`, `cosf` o `cosl`), o el coseno hiperbólico (`cosh`, `coshf` o `coshl`).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double cos(   
   double x   
);  
float cos(  
   float x   
);  // C++ only  
long double cos(  
   long double x  
);  // C++ only  
float cosf(   
   float x   
);  
long double cosl(  
   long double x  
);  
double cosh(   
   double x   
);  
float cosh(  
   float x   
);  // C++ only  
long double cosh(  
   long double x  
);  // C++ only  
float coshf(  
   float x   
);  
long double coshl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Ángulo en radianes.  
  
## <a name="return-value"></a>Valor devuelto  
 Coseno o coseno hiperbólico de `x`. Si `x` es mayor o igual que 263, o menor o igual a -263, una pérdida de significado en el resultado de una llamada a `cos`, `cosf`, o `cosl` se produce.  
  
 De forma predeterminada, si el resultado es demasiado grande en una llamada de `cosh`, `coshf` o `coshl`, la función devuelve `HUGE_VAL` y establece `errno` en `ERANGE`.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-----------|-------------------|-----------------------|  
|± `QNAN`,`IND`|ninguna|`_DOMAIN`|  
|± ∞  (`cosf`, `cos`, `cosl`)|`INVALID`|`_DOMAIN`|  
|x ≥ 7,104760e+002 (`cosh`, `coshf`, `coshl`)|`INEXACT`+`OVERFLOW`|`OVERFLOW`|  
  
## <a name="remarks"></a>Comentarios  
 Dado que C++ permite las sobrecargas, puede llamar a las sobrecargas de `cos` y `cosh` que toman y devuelven los valores `float` o `long double`. En un programa de C, `cos` y `cosh` siempre toman y devuelven `double`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`cos`, `cosh`, `cosf`, `coshf`, `cosl`, `coshl`|\<math.h>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Consulte el ejemplo de [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)   
 [_CIcos](../../c-runtime-library/cicos.md)
