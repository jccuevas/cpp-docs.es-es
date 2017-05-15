---
title: shuffle_order_engine (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- shuffle_order_engine
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- shuffle_order_engine class
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
caps.latest.revision: 17
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
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 93c5721a4b651315bc4d67cc9d5a0cb7d2f852a3
ms.contentlocale: es-es
ms.lasthandoff: 04/19/2017

---
# <a name="shuffleorderengine-class"></a>shuffle_order_engine (Clase)
Genera una secuencia aleatoria reordenando los valores que devuelve su motor base.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class Engine, size_t K>  
class shuffle_order_engine;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `Engine`  
 El tipo de motor base.  
  
 `K`  
 **Tamaño de la tabla**. Número de elementos en el búfer (tabla). **Condición previa**: `0 < K`  
  
## <a name="members"></a>Miembros  
  
||||  
|-|-|-|  
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|  
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|  
  
 Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de plantilla describe un *adaptador de motor* que genera valores reordenando los valores que su motor base devuelve. Cada constructor rellena la tabla interna con los valores `K` que el motor base ha devuelto y, cuando se solicita un valor, se selecciona un elemento aleatorio de la tabla.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<random>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [\<random>](../standard-library/random.md)


