---
title: Clase independent_bits_engine | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::independent_bits_engine
dev_langs:
- C++
helpviewer_keywords:
- independent_bits_engine class
ms.assetid: 889e9a82-f457-49a7-9d2e-26e0fc3cd907
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eb76c477c54192dc6b6b969ecd4cdd32850c015f
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110310"
---
# <a name="independentbitsengine-class"></a>independent_bits_engine (Clase)

Genera una secuencia aleatoria de números con un número específico de bits volviendo a empaquetar bits de los valores devueltos por su motor base.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Engine, size_t W, class UIntType>
class independent_bits_engine;
```

### <a name="parameters"></a>Parámetros

*Motor de*<br/>
El tipo de motor base.

*W*<br/>
**Tamaño de palabra**. Tamaño, en bits, de cada número generado. **Condición previa:** `0 < W ≤ numeric_limits<UIntType>::digits`

*UIntType*<br/>
El tipo de resultado integral sin signo. Para obtener información sobre los tipos posibles, vea [\<random>](../standard-library/random.md).

## <a name="members"></a>Miembros

||||
|-|-|-|
|`independent_bits_engine::independent_bits_engine`|`independent_bits_engine::base`|`independent_bits_engine::discard`|
|`independent_bits_engine::operator()`|`independent_bits_engine::base_type`|`independent_bits_engine::seed`|

Para obtener más información sobre los miembros del motor, vea [\<random>](../standard-library/random.md).

## <a name="remarks"></a>Comentarios

Esta clase de plantilla describe un *adaptador de motor* que produce valores volviendo a empaquetar bits de los valores devueltos por su motor base, lo que resulta en *W*-valores de bit.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<random>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[\<random>](../standard-library/random.md)<br/>
