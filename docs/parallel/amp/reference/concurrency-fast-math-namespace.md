---
title: Namespace fast_math | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_math/Concurrency::fast_math
dev_langs:
- C++
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d8a94b0911b772f4972416722757bec24a4826ed
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="concurrencyfastmath-namespace"></a>Concurrency::fast_math (Espacio de nombres)
Las funciones en el `fast_math` espacio de nombres tienen una menor precisión admite sólo de precisión simple (`float`) y llamar a las funciones intrínsecas de DirectX. Hay dos versiones de cada función, por ejemplo `cos` y `cosf`. Ambas toman y devuelven un `float`, pero cada uno de ellos llama a la misma DirectX intrínseco.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
namespace fast_math;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="functions"></a>Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcula el arco coseno del argumento|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcula el arco coseno del argumento|  
|[asin](concurrency-fast-math-namespace-functions.md#asin)|Calcula el arco seno del argumento|  
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|Calcula el arco seno del argumento|  
|[atan](concurrency-fast-math-namespace-functions.md#atan)|Calcula el arco tangente del argumento|  
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|Calcula el arco tangente de _Y/_X|  
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|Calcula el arco tangente de _Y/_X|  
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|Calcula el arco tangente del argumento|  
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|Calcula el límite superior del argumento|  
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|Calcula el límite superior del argumento|  
|[cos](concurrency-fast-math-namespace-functions.md#cos)|Calcula el coseno del argumento|  
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|Calcula el coseno del argumento|  
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|Calcula el valor de coseno hiperbólico del argumento|  
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|Calcula el valor de coseno hiperbólico del argumento|  
|[exp](concurrency-fast-math-namespace-functions.md#exp)|Calcula la base e exponencial del argumento|  
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|Calcula el valor exponencial del argumento de base&2;|  
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|Calcula el valor exponencial del argumento de base&2;|  
|[expf](concurrency-fast-math-namespace-functions.md#expf)|Calcula la base e exponencial del argumento|  
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|Devuelve el valor absoluto del argumento|  
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|Devuelve el valor absoluto del argumento|  
|[floor](concurrency-fast-math-namespace-functions.md#floor)|Calcula el límite inferior del argumento|  
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|Calcula el límite inferior del argumento|  
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|Determinar el valor numérico máximo de los argumentos|  
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|Determinar el valor numérico máximo de los argumentos|  
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|Determinar el valor numérico mínimo de los argumentos|  
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|Determinar el valor numérico mínimo de los argumentos|  
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|Calcula el resto de punto flotante de _X/_Y|  
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|Calcula el resto de punto flotante de _X/_Y|  
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|Obtiene la mantisa y el exponente de _X|  
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|Obtiene la mantisa y el exponente de _X|  
|[isFinite](concurrency-fast-math-namespace-functions.md#isfinite)|Determina si el argumento tiene un valor finito|  
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|Determina si el argumento es un infinito|  
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|Determina si el argumento es un NaN|  
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|Calcula un número real de la mantisa y exponente|  
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|Calcula un número real de la mantisa y exponente|  
|[log](concurrency-fast-math-namespace-functions.md#log)|Calcula el logaritmo en base e de argumento|  
|[log10](concurrency-fast-math-namespace-functions.md#log10)|Calcula el logaritmo en base&10; del argumento|  
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|Calcula el logaritmo en base&10; del argumento|  
|[log2](concurrency-fast-math-namespace-functions.md#log2)|Calcula el logaritmo en base&2; del argumento|  
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|Calcula el logaritmo en base&2; del argumento|  
|[logf](concurrency-fast-math-namespace-functions.md#logf)|Calcula el logaritmo en base e de argumento|  
|[modf](concurrency-fast-math-namespace-functions.md#modf)|Divide _X en fracciones y partes enteras.|  
|[modff](concurrency-fast-math-namespace-functions.md#modff)|Divide _X en fracciones y partes enteras.|  
|[pow](concurrency-fast-math-namespace-functions.md#pow)|Calcula _X elevado a la potencia de _Y|  
|[powf](concurrency-fast-math-namespace-functions.md#powf)|Calcula _X elevado a la potencia de _Y|  
|[round](concurrency-fast-math-namespace-functions.md#round)|Redondea _X al entero más próximo|  
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|Redondea _X al entero más próximo|  
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|Devuelve el inverso de la raíz cuadrada del argumento|  
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|Devuelve el inverso de la raíz cuadrada del argumento|  
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|Devuelve el signo del argumento|  
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|Devuelve el signo del argumento|  
|[sin](concurrency-fast-math-namespace-functions.md#sin)|Calcula el valor del seno del argumento|  
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|Calcula el seno y coseno el valor de _X|  
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|Calcula el seno y coseno el valor de _X|  
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|Calcula el valor del seno del argumento|  
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|Calcula el valor del seno hiperbólico del argumento|  
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|Calcula el valor del seno hiperbólico del argumento|  
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|Calcula la raíz cuadrada del argumento|  
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|Calcula la raíz cuadrada del argumento|  
|[tan](concurrency-fast-math-namespace-functions.md#tan)|Calcula el valor del argumento de tangente|  
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|Calcula el valor del argumento de tangente|  
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|Calcula el valor de la tangente hiperbólico del argumento|  
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|Calcula el valor de la tangente hiperbólico del argumento|  
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|Trunca el argumento para el componente de número entero|  
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|Trunca el argumento para el componente de número entero|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_math.h  
  
 **Namespace:** fast_math  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

