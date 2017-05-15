---
title: remquo, remquof, remquol | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
dev_langs:
- C++
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: fb7cbf4fe2450d574a4418e62c43dca699cde9b8
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="remquo-remquof-remquol"></a>remquo, remquof, remquol
Calcula el resto de dos valores enteros y almacena un valor entero con el signo y la magnitud aproximada del cociente en una ubicación que se especifica en un parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double remquo(   
   double numer,  
   double denom,  
   int* quo  
);  
float remquo(   
   float numer,  
   float denom,  
   int* quo  
); /* C++ only */  
long double remquo(   
   long double numer,  
   long double denom,  
   int* quo  
); /* C++ only */  
float remquof(   
   float numer,  
   float denom,  
   int* quo  
);  
long double remquol(   
   long double numer,  
   long double denom,  
   int* quo  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `numer`  
 Numerador.  
  
 `denom`  
 Denominador.  
  
 `quo`  
 Puntero a un entero para almacenar un valor que tiene el signo y la magnitud aproximada del cociente.  
  
## <a name="return-value"></a>Valor devuelto  
 `remquo` devuelve el resto de punto flotante de `x` / `y`. Si el valor de `y` es 0,0, `remquo` devuelve un valor NaN reservado. Para obtener información sobre la representación de un valor NaN reservado por la familia `printf`, vea [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `remquo` calcula el resto del punto flotante `f` de `x` / `y`, de manera que `x` = `i` `*` `y` + `f`, donde `i` es un entero, `f` tiene el mismo signo que `x` y el valor absoluto de `f` es menor que el valor absoluto de `y`.  
  
 Puesto que C++ permite las sobrecargas, es posible llamar a las sobrecargas de `remquo` que toman y devuelven los valores `float` o `long double`. En un programa C, `remquo` siempre toma dos valores Double y devuelve uno.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado necesario|  
|--------------|---------------------|  
|`remquo`, `remquof`, `remquol`|\<math.h>|  
  
 Para obtener información sobre la compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_remquo.c  
// This program displays a floating-point remainder.  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double w = -10.0, x = 3.0, z;  
   int quo = 0;  
  
   z = remquo(w, x, &quo);  
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);  
   printf("Approximate signed quotient is %d\n", quo);  
}  
```  
  
```Output  
The remainder of -10.00 / 3.00 is -1.000000  
Approximate signed quotient is -3  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ldiv, lldiv](../../c-runtime-library/reference/ldiv-lldiv.md)   
 [imaxdiv](../../c-runtime-library/reference/imaxdiv.md)   
 [fmod, fmodf](../../c-runtime-library/reference/fmod-fmodf.md)   
 [remainder, remainderf, remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)
