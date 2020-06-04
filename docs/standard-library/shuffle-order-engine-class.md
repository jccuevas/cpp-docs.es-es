---
title: shuffle_order_engine (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::shuffle_order_engine
- random/std::shuffle_order_engine::base
- random/std::shuffle_order_engine::discard
- random/std::shuffle_order_engine::operator()
- random/std::shuffle_order_engine::base_type
- random/std::shuffle_order_engine::seed
helpviewer_keywords:
- std::shuffle_order_engine [C++]
- std::shuffle_order_engine [C++], base
- std::shuffle_order_engine [C++], discard
- std::shuffle_order_engine [C++], base_type
- std::shuffle_order_engine [C++], seed
ms.assetid: 0bcd1fb0-44d7-4e59-bb1b-4a9b673a960d
ms.openlocfilehash: d72cfaae2e7f6768a68439fbc30aa5ab0d38f270
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686428"
---
# <a name="shuffle_order_engine-class"></a>shuffle_order_engine (Clase)

Genera una secuencia aleatoria reordenando los valores que devuelve su motor base.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Engine, size_t K>
class shuffle_order_engine;
```

### <a name="parameters"></a>Parámetros

@No__t_1 del *motor*
El tipo de motor base.

*K* \
**Tamaño de la tabla**. Número de elementos en el búfer (tabla). **Condición previa:** `0 < K`

## <a name="members"></a>Miembros

||||
|-|-|-|
|`shuffle_order_engine::shuffle_order_engine`|`shuffle_order_engine::base`|`shuffle_order_engine::discard`|
|`shuffle_order_engine::operator()`|`shuffle_order_engine::base_type`|`shuffle_order_engine::seed`|

Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

Esta plantilla de clase describe un *adaptador de motor* que genera valores reordenando los valores devueltos por su motor base. Cada constructor rellena la tabla interna con los valores *K* devueltos por el motor base, y se selecciona un elemento aleatorio de la tabla cuando se solicita un valor.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)
