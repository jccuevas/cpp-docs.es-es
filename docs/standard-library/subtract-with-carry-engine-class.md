---
title: "subtract_with_carry_engine (Clase) | Microsoft Docs"
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
  - "tr1.subtract_with_carry_engine"
  - "std::tr1::subtract_with_carry_engine"
  - "random/std::tr1::subtract_with_carry_engine"
  - "subtract_with_carry_engine"
  - "tr1::subtract_with_carry_engine"
  - "std.tr1.subtract_with_carry_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "subtract_with_carry_engine (clase)"
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: 20
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# subtract_with_carry_engine (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una secuencia aleatoria mediante el algoritmo resta por acarreo \(Fibonacci retrasado\).  
  
## Sintaxis  
  
```  
template<class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### Parámetros  
 `UIntType`  
 El tipo de resultado integral sin signo. Para los tipos posibles, consulte [\<random\>](../standard-library/random.md).  
  
 `W`  
 **Tamaño de palabra**. Tamaño de cada palabra, en bits, de la secuencia de estado.**Condición previa**: `0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **Intervalo corto**. Número de valores íntegros.**Condición previa**: `0 < S < R`  
  
 `R`  
 **Intervalo largo**. Determina la recurrencia en la serie generada.  
  
## Miembros  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed` es un miembro constante, definido como `19780503u`, utilizado como el valor de parámetro predeterminado para `subtract_with_carry_engine::seed` y el constructor de valores simple.|||  
  
 Para obtener más información acerca de los miembros del motor, consulte [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 La clase de plantilla `substract_with_carry_engine` es una mejora respecto al [linear\_congruential\_engine](../standard-library/linear-congruential-engine-class.md). Ninguno de estos motores es tan rápido o tiene unos resultados de mayor calidad que el [mersenne\_twister\_engine](../standard-library/mersenne-twister-engine-class.md).  
  
 Este motor produce valores de un tipo entero no asignado especificado por el usuario que utiliza la relación de recurrencia \(*periodo*\) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, en la que `cy(i)` tiene el valor `1` si `x(i - S) - x(i - R) - cy(i - 1) < 0`, de lo contrario `0` y `M` tiene el valor `2`<sup>W</sup>. El estado del motor es un indicador portador de más valores `R`. Estos valores consisten en los últimos valores `R` devueltos si `operator()` se ha llamado al menos `R` veces, de lo contrario, en los valores `N` que se han devuelto y los últimos valores `R - N`de la inicialización.  
  
 El argumento de la plantilla `UIntType` debe ser lo suficientemente grande para contener valores de hasta `M - 1`.  
  
 Aunque puede construir directamente un generador de este motor, también puede utilizar una de estas definiciones de tipos predefinidas:  
  
 `ranlux24_base`: Se usa como base para `ranlux24`.  
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`: Se usa como base para `ranlux48`.  
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 Para obtener información detallada sobre el algoritmo de resta con acarreo, vea el artículo de la Wikipedia [Generador de Fibonacci retardado](http://go.microsoft.com/fwlink/?LinkId=402445).  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)