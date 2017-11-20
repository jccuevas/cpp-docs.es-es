---
title: lgamma, lgammaf, lgammal | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- lgamma
- lgammaf
- lgammal
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
- lgamma
- lgammaf
- lgammal
- math/lgamma
- math/lgammaf
- math/lgammal
dev_langs: C++
helpviewer_keywords:
- lgamma function
- lgammal function
- lgammaf function
ms.assetid: 6e326c58-7077-481a-a329-c82ae56ae9e6
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: afc048d131bd75a9645c045b3bceae90344c07eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="lgamma-lgammaf-lgammal"></a>lgamma, lgammaf, lgammal
Determina el logaritmo natural del valor absoluto de la función gamma del valor especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double lgamma(  
   double x  
);  
  
float lgamma(  
   float x  
); //C++ only  
  
long double lgamma(  
   long double x  
); //C++ only  
  
float lgammaf(  
   float x  
);  
  
long double lgammal(  
   long double x  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `x`  
 Valor que se va a calcular.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve el logaritmo natural del valor absoluto de la función gamma de `x.`.  
  
|Problema|Volver|  
|-----------|------------|  
|`x` = NaN|NaN|  
|`x` = ±0|+INFINITY|  
|`x`= entero negativo|+INFINITY|  
|±INFINITY|+INFINITY|  
|error de polo|+HUGE_VAL, +HUGE_VALF o +HUGE_VALL|  
|error de intervalo de desbordamiento|±HUGE_VAL, ±HUGE_VALF o ±HUGE_VALL|  
  
 Los errores se notifican tal como se especifica en [_matherr](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Comentarios  
 Dado que C++ admite sobrecargas, puede llamar a las sobrecargas de `lgamma` que toman y devuelven los tipos float y long double. En un programa de C, `lgamma` siempre toma y devuelve un tipo double.  
  
 Si x es un número racional, esta función devuelve el logaritmo del factorial de (`x`-1).  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`lgamma`,                `lgammaf`,  `lgammal`|\<math.h>|\<cmath>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [tgamma, tgammaf, tgammal](../../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)