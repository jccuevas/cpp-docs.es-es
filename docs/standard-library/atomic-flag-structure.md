---
title: atomic_flag (Estructura)
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 36944c3c3bdc58272d87bbcdfb119d1c52c43995
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447402"
---
# <a name="atomicflag-structure"></a>atomic_flag (Estructura)

Describe un objeto que establece y borra de forma atómica una marca de **bool** . Las operaciones sobre marcas atómicas nunca tienen bloqueos.

## <a name="syntax"></a>Sintaxis

```cpp
struct atomic_flag;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[clear](#clear)|Establece la marca almacenada en **false**.|
|[test_and_set](#test_and_set)|Establece la marca almacenada en **true** y devuelve el valor de marca inicial.|

## <a name="remarks"></a>Comentarios

Se pueden pasar objetos `atomic_flag` a las funciones no miembro [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) y [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Se pueden inicializar con el valor `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> atómico

**Espacio de nombres:** std

## <a name="clear"></a>  atomic_flag::clear

Establece la marca **bool** que se almacena en `*this` **false**, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="test_and_set"></a>  atomic_flag::test_and_set

Establece la marca **bool** que se almacena en `*this` en **true**, dentro de las restricciones [memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor inicial de la marca que se almacena en `*this`.

## <a name="see-also"></a>Vea también

[\<atomic>](../standard-library/atomic.md)
