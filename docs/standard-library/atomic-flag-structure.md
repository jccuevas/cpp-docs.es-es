---
title: atomic_flag (Estructura)
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: ad4b6dcaf6db1a8abe5b81b4d630e84b54fbaa63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376867"
---
# <a name="atomic_flag-structure"></a>atomic_flag (Estructura)

Describe un objeto que establece y borra atómicamente una marca **bool.** Las operaciones sobre marcas atómicas nunca tienen bloqueos.

## <a name="syntax"></a>Sintaxis

```cpp
struct atomic_flag;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Claro](#clear)|Establece la marca almacenada en **false**.|
|[test_and_set](#test_and_set)|Establece la marca almacenada en **true** y devuelve el valor de marca inicial.|

## <a name="remarks"></a>Observaciones

Se pueden pasar objetos `atomic_flag` a las funciones no miembro [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear), [atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit), [atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) y [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit). Se pueden inicializar con el valor `ATOMIC_FLAG_INIT`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> atómica

**Espacio de nombres:** std

## <a name="atomic_flagclear"></a><a name="clear"></a>atomic_flag::claro

Establece el indicador **bool** `*this` que se almacena en **false**, dentro de las restricciones [de memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

## <a name="atomic_flagtest_and_set"></a><a name="test_and_set"></a>atomic_flag::test_and_set

Establece el indicador **bool** `*this` que se almacena en **true**, dentro de las restricciones [de memory_order](../standard-library/atomic-enums.md#memory_order_enum) especificadas.

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>Parámetros

*Orden*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum).

### <a name="return-value"></a>Valor devuelto

Valor inicial de la marca que se almacena en `*this`.

## <a name="see-also"></a>Consulte también

[\<>atómica](../standard-library/atomic.md)
