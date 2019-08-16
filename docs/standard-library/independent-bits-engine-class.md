---
title: independent_bits_engine (Clase)
ms.date: 11/04/2016
f1_keywords:
- random/std::independent_bits_engine
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
ms.openlocfilehash: a90e4be4ff6e92734f6b2e6804f8059be78e66b9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456342"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine (Clase)

Genera una secuencia aleatoria de números con un número específico de bits volviendo a empaquetar bits de los valores devueltos por su motor base.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parámetros

*Motor*\
El tipo de motor base.

*CON*\
**Tamaño de palabra**. Tamaño, en bits, de cada número generado. **Condición previa:** `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*\
El tipo de resultado integral sin signo. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

## <a name="members"></a>Miembros

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

Esta clase de plantilla describe un *adaptador de motor* que produce valores volviendo a empaquetar los bits de los valores devueltos por su motor base, lo que da como resultado valores de *W*-bit.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)
