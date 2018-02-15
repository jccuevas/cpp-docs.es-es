---
title: fdim, fdimf, fdiml | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
dev_langs:
- C++
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60e628f84dcadf7b1e214d526981191036428042
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fdim-fdimf-fdiml"></a>fdim, fdimf, fdiml
Determina la diferencia positiva entre el primer y el segundo valor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double fdim(  
   double x,   
   double y  
);  
  
float fdim(  
   float x,   
   float y  
); //C++ only  
  
long double fdim(  
   long double x,   
   long double y  
); //C++ only  
  
float fdimf(  
   float x,   
   float y  
);  
  
long double fdiml(  
   long double x,   
   long double y  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `x`  
 Primer valor.  
  
 [in] `y`  
 Segundo valor.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la diferencia positiva entre `x` y `y`:  
  
|Valor devuelto|Escenario|  
|------------------|--------------|  
|x-y|si x > y|  
|0|si x <= y|  
  
 De lo contrario, puede que devuelva uno de los siguientes errores:  
  
|Problema|Volver|  
|-----------|------------|  
|Error de intervalo de desbordamiento|+HUGE_VAL, +HUGE_VALF o +HUGE_VALL|  
|Error de intervalo de subdesbordamiento|valor correcto (después del redondeo)|  
|`x` o `y` es NaN|NaN|  
  
 Los errores se notifican tal como se especifica en [_matherr](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Comentarios  
 Dado que C++ admite sobrecargas, puede llamar a las sobrecargas de `fdim` que toman y devuelven los tipos float y long double. En un programa de C, `fdim` siempre toma y devuelve un tipo double.  
  
 Excepto para el control de NaN, esta función es equivalente a `fmax(x - y, 0)`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`fdim`, `fdimf`, `fdiml`|\<math.h>|\<cmath>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fmax, fmaxf, fmaxl](../../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)   
 [abs, labs, llabs, _abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)