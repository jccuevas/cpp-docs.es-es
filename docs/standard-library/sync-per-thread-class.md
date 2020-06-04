---
title: sync_per_thread (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
ms.openlocfilehash: 2976cdc6671750f0da439e9eb42053518e4af8d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376539"
---
# <a name="sync_per_thread-class"></a>sync_per_thread (Clase)

Describe un filtro de [sincronización](../standard-library/allocators-header.md) que proporciona un objeto de caché independiente para cada subproceso.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Cache>
class sync_per_thread
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Memoria caché*|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|

## <a name="remarks"></a>Observaciones

Los asignadores que usan `sync_per_thread` pueden ser iguales, aunque no se puede cancelar la asignación de bloques asignados en un subproceso desde otro subproceso. Cuando se usa uno de estos asignadores, los bloques de memoria asignados en un subproceso no deberían ser visibles para otros subprocesos. En la práctica, esto significa que un contenedor que usa uno de estos asignadores solo puede estar disponible para el acceso para un único subproceso.

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Asignar](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="sync_per_threadallocate"></a><a name="allocate"></a>sync_per_thread::asignar

Asigna un bloque de memoria.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*count*|El número de elementos de la matriz que se van a asignar.|

### <a name="remarks"></a>Observaciones

La función miembro devuelve el resultado de una llamada a `cache::allocate(count)` en el objeto de caché que pertenece al subproceso actual. Si no se asignó ningún objeto de caché para el subproceso actual, primero asigna uno.

## <a name="sync_per_threaddeallocate"></a><a name="deallocate"></a>sync_per_thread::deallocate

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

La función miembro llama a `deallocate` en el objeto de caché que pertenece al subproceso actual. Si no se asignó ningún objeto de caché para el subproceso actual, primero asigna uno.

## <a name="sync_per_threadequals"></a><a name="equals"></a>sync_per_thread::iguales

Compara dos cachés para determinar si son iguales.

```cpp
bool equals(const sync<Cache>& Other) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Memoria caché*|El objeto de caché del filtro de sincronización.|
|*Otros*|El objeto de caché para comparar la igualdad.|

### <a name="return-value"></a>Valor devuelto

**false** si no se ha asignado ningún objeto de caché para este objeto o para *Otro* en el subproceso actual. De lo contrario, devuelve el resultado de aplicar `operator==` a los dos objetos de caché.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
