---
title: rts_alloc (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
ms.openlocfilehash: 6ed84d906944a09fa355e281640e9480f3173554
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373427"
---
# <a name="rts_alloc-class"></a>rts_alloc (Clase)

La plantilla de clase rts_alloc describe un [filtro](../standard-library/allocators-header.md) que contiene una matriz de instancias de caché y determina qué instancia se va a utilizar para la asignación y desasignación en tiempo de ejecución en lugar de en tiempo de compilación.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Cache>
class rts_alloc
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Memoria caché*|El tipo de instancias de caché contenido en la matriz. Puede ser [cache_chunklist (Clase)](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md)|

## <a name="remarks"></a>Observaciones

Esta plantilla de clase contiene varias instancias de asignador de bloques y determina qué instancia se va a utilizar para la asignación o desasignación en tiempo de ejecución en lugar de en tiempo de compilación. Se usa con los compiladores que no se pueden reenlazar mediante compilación.

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Asignar](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="rts_allocallocate"></a><a name="allocate"></a>rts_alloc::asignar

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

La función `caches[_IDX].allocate(count)`miembro devuelve `_IDX` , donde el índice está determinado por el *recuento* `operator new(count)`de tamaño de bloque solicitado o, si *count* es demasiado grande, devuelve . `cache`, que representa el objeto de caché.

## <a name="rts_allocdeallocate"></a><a name="deallocate"></a>rts_alloc::deallocate

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

La función `caches[_IDX].deallocate(ptr, count)`miembro llama `_IDX` , donde el índice está determinado por el *recuento* `operator delete(ptr)`de tamaño de bloque solicitado o, si *count* es demasiado grande, devuelve .

## <a name="rts_allocequals"></a><a name="equals"></a>rts_alloc::igual es

Compara dos cachés para determinar si son iguales.

```cpp
bool equals(const sync<_Cache>& _Other) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*_Cache*|El objeto de caché asociado con el filtro.|
|*_Other*|El objeto de caché para comparar la igualdad.|

### <a name="remarks"></a>Observaciones

**true** si el `caches[0].equals(other.caches[0])`resultado de ; de lo contrario, **false**. `caches` representa la matriz de objetos de caché.

## <a name="see-also"></a>Consulte también

[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)\
[\<asignadores>](../standard-library/allocators-header.md)
