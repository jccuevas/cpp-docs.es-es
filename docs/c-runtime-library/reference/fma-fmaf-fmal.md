---
title: fma, fmaf, fmal | Microsoft Docs
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
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
dev_langs:
- C++
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: 59238cf511be936b0d882c2f00320ee7422904e0
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="fma-fmaf-fmal"></a>fma, fmaf, fmal
Multiplica dos valores juntos, agrega un tercer valor y luego redondea el resultado, sin perder ninguna precisión debido al redondeo intermedio.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
double fma(  
   double x,   
   double y,   
   double z  
);  
  
float fma(  
   float  x,   
   float  y,   
   float z  
); //C++ only  
  
long double fma(  
   long double  x,   
   long double  y,   
   long double z  
); //C++ only  
  
float fmaf(  
   float  x,   
   float  y,   
   float z  
);  
  
long double fmal(  
   long double  x,   
   long double  y,   
   long double z  
);  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `x`  
 Primer valor que se va a multiplicar.  
  
 [in] `y`  
 Segundo valor que se va a multiplicar.  
  
 [in] `z`  
 El valor que se va a agregar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `(x * y) + z`. El valor devuelto se redondea después con el formato de redondeo actual.  
  
 De lo contrario, es posible que devuelva uno de los siguientes valores:  
  
|Problema|Valor devuelto|  
|-----------|------------|  
|`x` = INFINITY, `y` = 0 o<br /><br /> `x` = 0, `y` = INFINITY|NaN|  
|`x` o `y` = exacto ±INFINITY, `z` = INFINITY con el signo opuesto|NaN|  
|`x` o `y` = NaN|NaN|  
|no (`x` = 0, `y`= indefinido) y `z` = NaN<br /><br /> no (`x`= indefinido, `y`=0) y `z` = NaN|NaN|  
|Error de intervalo de desbordamiento|±HUGE_VAL, ±HUGE_VALF o ±HUGE_VALL|  
|Error de intervalo de subdesbordamiento|valor correcto después del redondeo.|  
  
 Los errores se notifican tal como se especifica en [_matherr](../../c-runtime-library/reference/matherr.md).  
  
## <a name="remarks"></a>Comentarios  
 Como C++ permite las sobrecargas, puede llamar a sobrecargas de `fma` que toman y devuelven **float** y **long double** tipos. En un programa C, `fma` siempre toma y devuelve un **doble**.  
  
 Esta función calcula el valor como si fuera de precisión infinita y luego redondea el resultado final.  
  
## <a name="requirements"></a>Requisitos  
  
|Función|Encabezado C|Encabezado C++|  
|--------------|--------------|------------------|  
|`fma`, `fmaf`, `fmal`|\<math.h>|\<cmath>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [remainder, remainderf, remainderl](../../c-runtime-library/reference/remainder-remainderf-remainderl.md)   
 [remquo, remquof, remquol](../../c-runtime-library/reference/remquo-remquof-remquol.md)
