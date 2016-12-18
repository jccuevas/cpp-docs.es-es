---
title: "Concurrency::fast_math (Espacio de nombres) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_math/Concurrency::fast_math"
dev_langs: 
  - "C++"
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
caps.latest.revision: 9
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Concurrency::fast_math (Espacio de nombres)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Las funciones del espacio de nombres de `fast_math` tienen precisión inferior, solo admiten la precisión simple \(`float`\) y llama de forma intrínseca a DirectX.  Hay dos versiones de cada función, por ejemplo `cos` y `cosf`.  Ambas versiones toman y devuelven `float`, pero cada uno llama de la misma forma a DirectX.  
  
## Sintaxis  
  
```  
namespace fast_math;  
```  
  
## Miembros  
  
### Funciones  
  
|Name|Descripción|  
|----------|-----------------|  
|[cos \(Función\) \(fast\_math\)](../Topic/cos%20Function%20%20\(fast_math\).md)|Calcula el arcocoseno del argumento.|  
|[cosf \(Función\) \(fast\_math\)](../Topic/cosf%20Function%20\(fast_math\).md)|Calcula el arcocoseno del argumento.|  
|[asin \(Función\) \(fast\_math\)](../Topic/asin%20Function%20\(fast_math\).md)|Calcula el arcoseno del argumento.|  
|[asinf \(Función\) \(fast\_math\)](../Topic/asinf%20Function%20\(fast_math\).md)|Calcula el arcoseno del argumento.|  
|[atan \(Función\) \(fast\_math\)](../Topic/atan%20Function%20\(fast_math\).md)|Calcula el arcotangente del argumento.|  
|[atan2 \(Función\) \(fast\_math\)](../Topic/atan2%20Function%20\(fast_math\).md)|Calcula el arcotangente de \_Y\/\_X.|  
|[atan2f \(Función\) \(fast\_math\)](../Topic/atan2f%20Function%20\(fast_math\).md)|Calcula el arcotangente de \_Y\/\_X.|  
|[atanf \(Función\) \(fast\_math\)](../Topic/atanf%20Function%20\(fast_math\).md)|Calcula el arcotangente del argumento.|  
|[ceil \(Función\) \(fast\_math\)](../Topic/ceil%20Function%20\(fast_math\).md)|Calcula el múltiplo superior del argumento.|  
|[ceilf \(Función\) \(fast\_math\)](../Topic/ceilf%20Function%20\(fast_math\).md)|Calcula el múltiplo superior del argumento.|  
|[cos \(Función\) \(fast\_math\)](../Topic/cos%20Function%20%20\(fast_math\).md)|Calcula el coseno del argumento.|  
|[cosf \(Función\) \(fast\_math\)](../Topic/cosf%20Function%20\(fast_math\).md)|Calcula el coseno del argumento.|  
|[cosh \(Función\) \(fast\_math\)](../Topic/cosh%20Function%20\(fast_math\).md)|Calcula el valor del coseno hiperbólico del argumento.|  
|[coshf \(Función\) \(fast\_math\)](../Topic/coshf%20Function%20\(fast_math\).md)|Calcula el valor del coseno hiperbólico del argumento.|  
|[exp \(Función\) \(fast\_math\)](../Topic/exp%20Function%20\(fast_math\).md)|Calcula la base e exponencial del argumento.|  
|[exp2 \(Función\) \(fast\_math\)](../Topic/exp2%20Function%20\(fast_math\).md)|Calcula la exponencial en base 2 del argumento.|  
|[exp2f \(Función\) \(fast\_math\)](../Topic/exp2f%20Function%20\(fast_math\).md)|Calcula la exponencial en base 2 del argumento.|  
|[expf \(Función\) \(fast\_math\)](../Topic/expf%20Function%20\(fast_math\).md)|Calcula la base e exponencial del argumento.|  
|[fabs \(Función\) \(fast\_math\)](../Topic/fabs%20Function%20\(fast_math\).md)|Devuelve el valor absoluto del argumento|  
|[fabsf \(Función\) \(fast\_math\)](../Topic/fabsf%20Function%20\(fast_math\).md)|Devuelve el valor absoluto del argumento|  
|[floor \(Función\) \(fast\_math\)](../Topic/floor%20Function%20\(fast_math\).md)|Calcula el valor inferior del argumento.|  
|[floorf \(Función\) \(fast\_math\)](../Topic/floorf%20Function%20\(fast_math\).md)|Calcula el valor inferior del argumento.|  
|[fmax \(Función\) \(fast\_math\)](../Topic/fmax%20Function%20\(fast_math\).md)|Determina el máximo valor numérico de los argumentos|  
|[fmaxf \(Función\) \(fast\_math\)](../Topic/fmaxf%20Function%20\(fast_math\).md)|Determina el máximo valor numérico de los argumentos|  
|[fmin \(Función\) \(fast\_math\)](../Topic/fmin%20Function%20\(fast_math\).md)|Determina el mínimo valor numérico de los argumentos|  
|[fminf \(Función\) \(fast\_math\)](../Topic/fminf%20Function%20\(fast_math\).md)|Determina el mínimo valor numérico de los argumentos|  
|[fmod \(Función\) \(fast\_math\)](../Topic/fmod%20Function%20\(fast_math\).md)|Calcula el residuo del punto flotante de \_X\/\_Y.|  
|[fmodf \(Función\) \(fast\_math\)](../Topic/fmodf%20Function%20\(fast_math\).md)|Calcula el residuo del punto flotante de \_X\/\_Y.|  
|[frexp \(Función\) \(fast\_math\)](../Topic/frexp%20Function%20\(fast_math\).md)|Obtiene la mantisa y el exponente de \_X.|  
|[frexpf \(Función\) \(fast\_math\)](../Topic/frexpf%20Function%20\(fast_math\).md)|Obtiene la mantisa y el exponente de \_X.|  
|[isfinite \(Función\) \(fast\_math\)](../Topic/isfinite%20Function%20\(fast_math\).md)|Determina si el argumento tiene un valor finito|  
|[isinf \(Función\) \(fast\_math\)](../Topic/isinf%20Function%20\(fast_math\).md)|Determina si el argumento es infinito|  
|[isnan \(Función\) \(fast\_math\)](../Topic/isnan%20Function%20\(fast_math\).md)|Determina si el argumento es NaN|  
|[ldexp \(Función\) \(fast\_math\)](../Topic/ldexp%20Function%20\(fast_math\).md)|Calcula un número real a partir de la mantisa y el exponente.|  
|[ldexpf \(Función\) \(fast\_math\)](../Topic/ldexpf%20Function%20\(fast_math\).md)|Calcula un número real a partir de la mantisa y el exponente.|  
|[log \(Función\) \(fast\_math\)](../Topic/log%20Function%20\(fast_math\).md)|Calcula el logaritmo en base e del argumento.|  
|[log10 \(Función\) \(fast\_math\)](../Topic/log10%20Function%20\(fast_math\).md)|Calcula el logaritmo en base 10 del argumento.|  
|[log10f \(Función\) \(fast\_math\)](../Topic/log10f%20Function%20\(fast_math\).md)|Calcula el logaritmo en base 10 del argumento.|  
|[log2 \(Función\) \(fast\_math\)](../Topic/log2%20Function%20\(fast_math\).md)|Calcula el logaritmo en base 2 del argumento.|  
|[log2f \(Función\) \(fast\_math\)](../Topic/log2f%20Function%20\(fast_math\).md)|Calcula el logaritmo en base 2 del argumento.|  
|[logf \(Función\) \(fast\_math\)](../Topic/logf%20Function%20\(fast_math\).md)|Calcula el logaritmo en base e del argumento.|  
|[modf \(Función\) \(fast\_math\)](../Topic/modf%20Function%20\(fast_math\).md)|Divide \_X en fracciones y enteros.|  
|[modff \(Función\) \(fast\_math\)](../Topic/modff%20Function%20\(fast_math\).md)|Divide \_X en fracciones y enteros.|  
|[pow \(Función\) \(fast\_math\)](../Topic/pow%20Function%20\(fast_math\).md)|Calcula el valor de \_X elevado a la potencia \_Y|  
|[powf \(Función\) \(fast\_math\)](../Topic/powf%20Function%20\(fast_math\).md)|Calcula el valor de \_X elevado a la potencia \_Y|  
|[round \(Función\) \(fast\_math\)](../Topic/round%20Function%20\(fast_math\).md)|Redondea \_X al entero más cercano|  
|[roundf \(Función\) \(fast\_math\)](../Topic/roundf%20Function%20\(fast_math\).md)|Redondea \_X al entero más cercano|  
|[rsqrt \(Función\) \(fast\_math\)](../Topic/rsqrt%20Function%20\(fast_math\).md)|Devuelve el valor recíproco de la raíz cuadrada del argumento|  
|[rsqrtf \(Función\) \(fast\_math\)](../Topic/rsqrtf%20Function%20\(fast_math\).md)|Devuelve el valor recíproco de la raíz cuadrada del argumento|  
|[signbit \(Función\) \(fast\_math\)](../Topic/signbit%20Function%20\(fast_math\).md)|Devuelve el signo del argumento|  
|[signbitf \(Función\) \(fast\_math\)](../Topic/signbitf%20Function%20\(fast_math\).md)|Devuelve el signo del argumento|  
|[sin \(Función\) \(fast\_math\)](../Topic/sin%20Function%20\(fast_math\).md)|Calcula el valor del seno del argumento.|  
|[sincos \(Función\) \(fast\_math\)](../Topic/sincos%20Function%20\(fast_math\).md)|Calcula el valor del seno y el coseno de \_X|  
|[sincosf \(Función\) \(fast\_math\)](../Topic/sincosf%20Function%20\(fast_math\).md)|Calcula el valor del seno y el coseno de \_X|  
|[sinf \(Función\) \(fast\_math\)](../Topic/sinf%20Function%20\(fast_math\).md)|Calcula el valor del seno del argumento.|  
|[sinh \(Función\) \(fast\_math\)](../Topic/sinh%20Function%20\(fast_math\).md)|Calcula el valor hiperbólico del seno del argumento.|  
|[sinhf \(Función\) \(fast\_math\)](../Topic/sinhf%20Function%20\(fast_math\).md)|Calcula el valor hiperbólico del seno del argumento.|  
|[sqrt \(Función\) \(fast\_math\)](../Topic/sqrt%20Function%20\(fast_math\).md)|Calcula la raíz cuadrada del argumento.|  
|[sqrtf \(Función\) \(fast\_math\)](../Topic/sqrtf%20Function%20\(fast_math\).md)|Calcula la raíz cuadrada del argumento.|  
|[tan \(Función\) \(fast\_math\)](../Topic/tan%20Function%20\(fast_math\).md)|Calcula el valor de la tangente del argumento.|  
|[tanf \(Función\) \(fast\_math\)](../Topic/tanf%20Function%20\(fast_math\).md)|Calcula el valor de la tangente del argumento.|  
|[tanh \(Función\) \(fast\_math\)](../Topic/tanh%20Function%20\(fast_math\).md)|Calcula el valor de la tangente hiperbólica del argumento.|  
|[tanhf \(Función\) \(fast\_math\)](../Topic/tanhf%20Function%20\(fast_math\).md)|Calcula el valor de la tangente hiperbólica del argumento.|  
|[trunc \(Función\) \(fast\_math\)](../Topic/trunc%20Function%20\(fast_math\).md)|Trunca el argumento del componente entero|  
|[truncf \(Función\) \(fast\_math\)](../Topic/truncf%20Function%20\(fast_math\).md)|Trunca el argumento del componente entero|  
  
## Requisitos  
 **Encabezado:** amp\_math.h  
  
 **Espacio de nombres:** Concurrency::fast\_math  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)