---
title: discard_block_engine (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::discard_block_engine
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
ms.openlocfilehash: 76a78a2f47bd160c6b2b981b1ccdda2ef3a90575
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454393"
---
# <a name="discardblockengine-class"></a>discard_block_engine (Clase)

Genera una secuencia aleatoria descartando valores devueltos por su motor base.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parámetros

*Motor*\
El tipo de motor base.

*M*\
**Tamaño de bloque**. El número de valores de cada bloque.

*R*\
**Bloque usado**. El número de valores de cada bloque que se utilizan. El resto se descartan (`P` - `R`). **Condición previa:** `0 < R ≤ P`

## <a name="members"></a>Miembros

||||
|-|-|-|
|`discard_block_engine::discard_block_engine`|`discard_block_engine::base`|`discard_block_engine::discard`|
|`discard_block_engine::operator()`|`discard_block_engine::base_type`|`discard_block_engine::seed`|

Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

Esta clase de plantilla describe un adaptador de motor que produce valores descartando algunos de los valores devueltos por su motor base.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)
