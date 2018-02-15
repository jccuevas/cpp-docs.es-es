---
title: expm1, expm1f, expm1l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 85fc89810e37236b4e7e4844931393395f51426d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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
 [exp2, exp2f, exp2l](exp2-exp2f-exp2l.md)   
 [pow, powf, powl](../../c-runtime-library/reference/pow-powf-powl.md)