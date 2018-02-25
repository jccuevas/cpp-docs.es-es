---
title: Clase independent_bits_engine | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d2f5b064b91aa6df766ff4ca460a6096f984ab8b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="independentbitsengine-class"></a>independent_bits_engine (Clase)
Genera una secuencia aleatoria de números con un número específico de bits volviendo a empaquetar bits de los valores devueltos por su motor base.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Engine, size_t W, class UIntType>  
class independent_bits_engine;  
```  
  
### <a name="parameters"></a>Parámetros  
 `Engine`  
 El tipo de motor base.  
  
 `W`  
 **Tamaño de palabra**. Tamaño, en bits, de cada número generado. **Condición previa:** `0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `UIntType`  
 El tipo de resultado integral sin signo. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).  
  
## <a name="members"></a>Miembros  
  
||||  
|-|-|-|  
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|  
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|  
  
 Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de plantilla describe un *adaptador de motor* que produce valores volviendo a empaquetar bits de los valores devueltos por su motor base, lo que resulta en valores de `W` bits.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<random>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<random>](../standard-library/random.md)

