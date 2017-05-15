---
title: expm1, expm1f, expm1l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
dev_langs:
- C++
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
caps.latest.revision: 4
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
ms.openlocfilehash: 0ebd79ed048bad988ca8a31f0f2f8d5427b84675
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="expm1-expm1f-expm1l"></a>expm1, expm1f, expm1l
Calcula el valor exponencial en base e de un valor, menos uno.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double expm1(   
   double x   
);  
float expm1(  
   float x  
);  // C++ only  
long double expm1(  
   long double x  
);  // C++ only  
float expm1f(  
   float x  
);  
long double expm1l(  
   long double x  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor exponencial del punto flotante.  
  
## <a name="return-value"></a>Valor devuelto  
 El `expm1` funciones devuelven un valor de punto flotante que representa e<sup>x</sup> - 1, si se realiza correctamente. En caso de desbordamiento, `expm1` devuelve `HUGE_VAL`, `expm1f` devuelve `HUGE_VALF`, `expm1l` devuelve `HUGE_VALL` y `errno` se establece en `ERANGE`. Para obtener más información sobre los códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 Puesto que C++ permite las sobrecargas, es posible llamar a las sobrecargas de `expm1` que toman y devuelven los valores `float` y `long double`. En un programa C, `expm1` siempre y devuelve `double`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`expm1`, `expm1f`, `expm1l`|\<math.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [exp2, exp2f, exp2l](http://msdn.microsoft.com/en-us/a7974629-be1e-4196-a562-6624a0732003)   
 [pow, powf, powl](../../c-runtime-library/reference/pow-powf-powl.md)
