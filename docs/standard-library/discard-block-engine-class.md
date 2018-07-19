---
title: discard_block_engine (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- random/std::discard_block_engine
dev_langs:
- C++
helpviewer_keywords:
- discard_block_engine class
ms.assetid: aa84808e-38fe-4fa0-9f73-d5b9a653345b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b65cfbe156ba462af9e87abf82d63023cfdc44b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957443"
---
# <a name="discardblockengine-class"></a>discard_block_engine (Clase)

Genera una secuencia aleatoria descartando valores devueltos por su motor base.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Engine, size_t P, size_t R>
class discard_block_engine;
```

### <a name="parameters"></a>Parámetros

*Motor* el tipo de motor de base.

*P* **tamaño de bloque**. El número de valores de cada bloque.

*R* **bloque usado**. El número de valores de cada bloque que se utilizan. El resto se descartan (`P` - `R`). **Condición previa:** `0 < R ≤ P`

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

[\<random>](../standard-library/random.md)<br/>
