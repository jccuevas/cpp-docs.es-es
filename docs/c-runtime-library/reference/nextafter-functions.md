---
title: nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
dev_langs: C++
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 798e39624c617d8178a7598e74451ca2851cfe12
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="nextafter-nextafterf-nextafterl-nextafter-nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter, nextafterf, nextafterl, _nextafter, _nextafterf, nexttoward, nexttowardf, nexttowardl
Devuelve el siguiente valor de punto flotante que se pueda representar.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double nextafter(  
   double x,  
   double y   
);  
  
float nextafter(  
   float x,  
   float y   
); /* C++ only, requires <cmath> */  
  
long double nextafter(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nextafterf(  
   float x,  
   float y   
);   
  
long double nextafterl(  
   long double x,  
   long double y   
);  
  
double _nextafter(  
   double x,  
   double y   
);  
  
float _nextafterf(  
   float x,  
   float y   
); /* x64 only */  
  
double nexttoward(  
   double x,  
   long double y   
);  
  
float nexttoward(  
   float x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
long double nexttoward(  
   long double x,  
   long double y   
); /* C++ only, requires <cmath> */  
  
float nexttowardf(  
   float x,  
   long double y   
);   
  
long double nexttowardl(  
   long double x,  
   long double y   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante del que se va a comenzar.  
  
 `y`  
 Valor de punto flotante al que se va.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el siguiente valor de punto flotante representable del tipo de valor devuelto después de `x` en la dirección de `y`. Si `x`=`y`, la función devuelve `y`, convertido en el tipo de valor devuelto, sin ninguna excepción activada. Si `x` no es igual a `y` y el resultado es cero o un valor desnormalizado, se establecen los estados de excepción de punto flotante FE_UNDERFLOW y FE_INEXACT y se devuelve el resultado correcto. Si `x` o `y` es un NaN, el valor devuelto es uno de los NaN de entrada. Si `x` es finito y el resultado es infinito o no se puede representar en el tipo, se devuelve un infinito o NaN con el signo correcto, se establecen los estados de excepción de punto flotante FE_OVERFLOW y FE_INEXACT y `errno` se establece en ERANGE.  
  
## <a name="remarks"></a>Comentarios  
 Las familias de las funciones `nextafter` y `nexttoward` son equivalentes, salvo por el tipo de parámetro de `y`. Si `x` y `y` son iguales, el valor devuelto es `y` convertido al tipo de valor devuelto.  
  
 Como C++ permite las sobrecargas, si incluye \<cmath>, puede llamar a las sobrecargas de `nextafter` y `nexttoward`, que devuelven los tipos `float` y `long double`. En un programa de C, `nextafter` y `nexttoward` siempre devuelven `double`.  
  
 Las funciones `_nextafter` y `_nextafterf` son específicas de Microsoft. La función `_nextafterf` solo está disponible cuando se compila para x64.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario (C)|Encabezado necesario (C++)|  
|-------------|---------------------------|-------------------------------|  
|`nextafter`, `nextafterf`, `nextafterl`, `_nextafterf`, `nexttoward`, `nexttowardf`, `nexttowardl`|\<math.h>|\<math.h> o \<cmath>|  
|`_nextafter`|\<float.h>|\<float.h> o \<cfloat>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isnan, _isnan, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)