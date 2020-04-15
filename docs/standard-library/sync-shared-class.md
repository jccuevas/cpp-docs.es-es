---
title: sync_shared (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
ms.openlocfilehash: 029edea59f29534491232d5d99353ccb093447bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376533"
---
# <a name="sync_shared-class"></a>sync_shared (Clase)

Describe un filtro de [sincronización](../standard-library/allocators-header.md) que usa una exclusión mutua para controlar el acceso a un objeto de caché compartido por todos los asignadores.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Memoria caché*|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Asignar](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="sync_sharedallocate"></a><a name="allocate"></a>sync_shared::asignar

Asigna un bloque de memoria.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*count*|El número de elementos de la matriz que se van a asignar.|

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto asignado.

### <a name="remarks"></a>Observaciones

La función miembro bloquea la exclusión mutua, llama a `cache.allocate(count)`, desbloquea la exclusión mutua y devuelve el resultado de la llamada anterior a `cache.allocate(count)`. `cache` representa el objeto de caché actual.

## <a name="sync_shareddeallocate"></a><a name="deallocate"></a>sync_shared::deallocate

Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Ptr*|Un puntero al primer objeto que se va a desasignar del almacenamiento.|
|*count*|El número de objetos que se van a desasignar del almacenamiento.|

### <a name="remarks"></a>Observaciones

Esta función miembro bloquea la exclusión mutua, llama a `cache.deallocate(ptr, count)`, donde `cache` representa el objeto de caché y, después, desbloquea la exclusión mutua.

## <a name="sync_sharedequals"></a><a name="equals"></a>sync_shared::igual es

Compara dos cachés para determinar si son iguales.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Memoria caché*|El tipo de caché asociado al filtro de sincronización.|
|*Otros*|La caché para comparar la igualdad.|

### <a name="return-value"></a>Valor devuelto

**true** si el `cache.equals(Other.cache)`resultado `cache` de , donde representa el objeto de caché, es **true**; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
