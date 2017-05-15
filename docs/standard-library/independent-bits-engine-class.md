---
title: Clase independent_bits_engine | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- independent_bits_engine
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
caps.latest.revision: 17
author: corob-msft
ms.author: corob
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
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 9a4052e44457b08f7d74f3591bd8665f0679c9a5
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

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
 **Tamaño de palabra**. Tamaño, en bits, de cada número generado. **Condición previa**: `0 < W ≤ numeric_limits<UIntType>::digits`  
  
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


