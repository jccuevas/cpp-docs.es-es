---
title: subtract_with_carry_engine (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs: C++
helpviewer_keywords:
- std::subtract_with_carry_engine [C++]
- std::subtract_with_carry_engine [C++], default_seed
- std::subtract_with_carry_engine [C++], discard
- std::subtract_with_carry_engine [C++], min
- std::subtract_with_carry_engine [C++], max
- std::subtract_with_carry_engine [C++], seed
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8de1c19ac793dd78ee55a15bc1156408936174bc
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine (Clase)
Genera una secuencia aleatoria mediante el algoritmo resta por acarreo (Fibonacci retrasado).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `UIntType`  
 El tipo de resultado integral sin signo. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
 `W`  
 **Tamaño de palabra**. Tamaño de cada palabra, en bits, de la secuencia de estado. **Condición previa:** `0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **Intervalo corto**. Número de valores íntegros. **Condición previa:** `0 < S < R`  
  
 `R`  
 **Intervalo largo**. Determina la recurrencia en la serie generada.  
  
## <a name="members"></a>Miembros  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed` es un miembro constante, definido como `19780503u`, utilizado como el valor de parámetro predeterminado para `subtract_with_carry_engine::seed` y el constructor de valores simple.|||  
  
 Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla `substract_with_carry_engine` es una mejora respecto al [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md). Ninguno de estos motores es tan rápido o tiene unos resultados de mayor calidad que el [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md).  
  
 Este motor produce valores de un tipo entero sin signo especificado por el usuario que usa la relación de periodicidad ( *periodo*) `x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`, en la que `cy(i)` tiene el valor `1` si `x(i - S) - x(i - R) - cy(i - 1) < 0`. De lo contrario `0`, y `M` tiene el valor `2`<sup>W</sup>. El estado del motor es un indicador portador de más valores `R`. Estos valores consisten en los últimos valores `R` devueltos si `operator()` se ha llamado al menos `R` veces, de lo contrario, en los valores `N` que se han devuelto y los últimos valores `R - N`de la inicialización.  
  
 El argumento de la plantilla `UIntType` debe ser lo suficientemente grande para contener valores de hasta `M - 1`.  
  
 Aunque puede construir un generador directamente a partir de este motor, también puede usar una de estas definiciones de tipos predefinidas:  
  
 `ranlux24_base`: se usa como base para `ranlux24`.                   
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`: se usa como base para `ranlux48`.                   
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 Para más detalles sobre el algoritmo de motor de resta con llevadas, vea el artículo de la Wikipedia sobre el [generador de Fibonacci retardado](http://go.microsoft.com/fwlink/p/?linkid=402445).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<random>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<random>](../standard-library/random.md)

