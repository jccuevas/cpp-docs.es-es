---
title: fpclassify | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- fpclassify
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
apitype: HeaderDef
f1_keywords:
- fpclassify
- math/fpclassify
helpviewer_keywords:
- fpclassify macro
- fpclassify function
ms.assetid: bf549499-7ff9-4a58-8692-f2d1cb6bab81
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81a2c9c5237d455908e1d0e4f58bff87418a7f8b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="fpclassify"></a>fpclassify
Devuelve la clasificación de punto flotante del argumento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int fpclassify(   
   /* floating-point */ x   
);  
  
int fpclassify(   
   float x   
); // C++ only  
  
int fpclassify(   
   double x   
); // C++ only  
  
int fpclassify(   
   long double x   
); // C++ only  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `x`  
 Valor de punto flotante que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 La función `fpclassify` devuelve un valor entero que indica la clasificación de punto flotante del argumento `x`. Esta tabla muestra los posibles valores devueltos por `fpclassify`, que se definen en \<math.h>.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`FP_NAN`|NaN reservado, de señalización o indeterminado|  
|`FP_INFINITE`|Infinito positivo o negativo|  
|`FP_NORMAL`|Valor positivo o negativo normalizado distinto de cero|  
|`FP_SUBNORMAL`|Valor positivo o negativo no normalizado|  
|`FP_ZERO`|Valor cero positivo o negativo|  
  
## <a name="remarks"></a>Comentarios  
 En C, `fpclassify` es una macro; en C++, `fpclassify` es una función sobrecargada con tipos de argumento de `float`, `double` o `long double`. En cualquier caso, el valor devuelto depende del tipo efectivo de la expresión de argumento y no de alguna representación intermedia. Por ejemplo, un valor `double` o `long double` normal puede convertirse en un valor infinito, no normalizado o cero cuando se convierte en un `float`.  
  
## <a name="requirements"></a>Requisitos  
  
|Función o macro|Encabezado necesario (C)|Encabezado necesario (C++)|  
|---------------------|---------------------------|-------------------------------|  
|`fpclassify`|\<math.h>|\<math.h> o \<cmath>|  
  
 La macro `fpclassify` y las funciones `fpclassify` se ajustan a las especificaciones C99 y C++11. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [isnan, _isnan, _isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)