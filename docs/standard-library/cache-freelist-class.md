---
title: cache_freelist (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
ms.openlocfilehash: 05260d6800597b64908ff0aeffac47b09fed9a0e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449688"
---
# <a name="cachefreelist-class"></a>cache_freelist (Clase)

Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Sz*|El número de elementos de la matriz que se van a asignar.|
|*Max*|La clase máxima que representa el tamaño máximo de la lista libre. Esta puede ser [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) o [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Comentarios

La clase de plantilla cache_freelist mantiene una lista libre de bloques de memoria de tamaño *SZ*. Cuando la lista libre está completa, usa el **operador Delete** para desasignar bloques de memoria. Cuando la lista libre está vacía, usa el **operador New** para asignar nuevos bloques de memoria. El tamaño máximo de la lista libre viene determinado por la clase Max Class pasada en el parámetro *Max* .

Cada bloque de memoria contiene *SZ* bytes de memoria utilizable y los datos que el **operador New** y el **operador Delete** requieren.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[cache_freelist](#cache_freelist)|Construye un objeto de tipo `cache_freelist`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[allocate](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="allocate"></a>  cache_freelist::allocate

Asigna un bloque de memoria.

```cpp
void *allocate(std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*count*|El número de elementos de la matriz que se van a asignar.|

### <a name="return-value"></a>Valor devuelto

Un puntero al objeto asignado.

### <a name="remarks"></a>Comentarios

## <a name="cache_freelist"></a>  cache_freelist::cache_freelist

Construye un objeto de tipo `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Comentarios

## <a name="deallocate"></a>  cache_freelist::deallocate

Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*ptr*|Un puntero al primer objeto que se va a desasignar del almacenamiento.|
|*count*|El número de objetos que se van a desasignar del almacenamiento.|

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
