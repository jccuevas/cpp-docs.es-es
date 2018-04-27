---
title: atomic_flag (Estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
dev_langs:
- C++
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f36164427f7cbc1cea9fda5f7e4d20896323d08
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="atomicflag-structure"></a>atomic_flag (Estructura)

Describe un objeto que establece y borra una marca `bool` de forma atómica. Las operaciones sobre marcas atómicas nunca tienen bloqueos.

## <a name="syntax"></a>Sintaxis

```cpp
struct atomic_flag;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[clear](#clear)|Establece la marca almacenada en `false`.|
|[test_and_set](#test_and_set)|Establece la marca almacenada en `true` y devuelve el valor inicial de la marca.|

## <a name="remarks"></a>Comentarios

Se pueden pasar objetos `atomic_flag` a las funciones no miembro [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) y [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Se pueden inicializar con el valor `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<atómica >

**Espacio de nombres:** std

## <a name="clear"></a>  atomic_flag:: Clear

Establece la marca `bool` almacenada en `*this` en `false`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parámetros

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag:: test_and_set

Establece la marca `bool` almacenada en `*this` en `true`, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parámetros

`Order` A [memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor inicial de la marca que se almacena en `*this`.

## <a name="see-also"></a>Vea también

[\<atomic>](../standard-library/atomic.md)<br/>
