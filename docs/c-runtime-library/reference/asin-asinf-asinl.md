---
title: asin, asinf, asinl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- asinf
- asinl
- asin
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
- asin
- asinl
- asinf
dev_langs:
- C++
helpviewer_keywords:
- asin function
- asinl function
- asinf function
- trigonometric functions
- arcsine function
ms.assetid: ca05f9ea-b711-49f6-9f32-2f4019abfd69
caps.latest.revision: 14
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
ms.openlocfilehash: c0bdcd8c1372f49c03e3ada06e98fcfd36815196
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="asin-asinf-asinl"></a>asin, asinf, asinl
Calcula el arcoseno.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double asin(   
   double x   
);  
float asin(  
   float x  
);  // C++ only  
long double asin(  
   long double x  
);  // C++ only  
float asinf (   
   float x   
);  
long double asinl(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor cuyo arcoseno se va a calcular.  
  
## <a name="return-value"></a>Valor devuelto  
 El `asin` función devuelve el arco seno (función de seno inverso) de `x` en el intervalo de - π/2 a π/2 radianes.  
  
 De forma predeterminada, si `x` es menor que -1 o mayor que 1, `asin` devuelve un indefinido.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-----------|-------------------|-----------------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± `QNAN`,`IND`|ninguna|`_DOMAIN`|  
|&#124;x&#124;>1|`INVALID`|`_DOMAIN`|  
  
## <a name="remarks"></a>Comentarios  
 Como C++ permite las sobrecargas, puede llamar a sobrecargas de `asin` con valores de `float` y `long double`. En un programa de C, `asin` siempre toma y devuelve un tipo double.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`asin`, `asinf`, `asinl`|\<math.h>|  
  
## <a name="example"></a>Ejemplo  
 Para obtener más información, consulte [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [acos, acosf, acosl](../../c-runtime-library/reference/acos-acosf-acosl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)
