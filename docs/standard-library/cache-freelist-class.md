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
ms.openlocfilehash: d757909d3e54fed35bf42b943b9f9740dffee115
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366747"
---
# <a name="cache_freelist-class"></a>cache_freelist (Clase)

Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, class Max>
class cache_freelist
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Sz*|El número de elementos de la matriz que se van a asignar.|
|*máximo*|La clase máxima que representa el tamaño máximo de la lista libre. Esta puede ser [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) o [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Observaciones

La plantilla de clase cache_freelist mantiene una lista gratuita de bloques de memoria de tamaño *Sz*. Cuando la lista gratuita está llena, utiliza **operator delete** para desasignar bloques de memoria. Cuando la lista gratuita está vacía, utiliza el **operador new** para asignar nuevos bloques de memoria. El tamaño máximo de la lista libre viene determinado por la clase max pasada en el parámetro *Max.*

Cada bloque de memoria contiene *bytes Sz* de memoria utilizable y los datos que requieren **el operador new** y el operador **delete.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[cache_freelist](#cache_freelist)|Construye un objeto de tipo `cache_freelist`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Asignar](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="cache_freelistallocate"></a><a name="allocate"></a>cache_freelist::asignar

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

## <a name="cache_freelistcache_freelist"></a><a name="cache_freelist"></a>cache_freelist::cache_freelist

Construye un objeto de tipo `cache_freelist`.

```cpp
cache_freelist();
```

### <a name="remarks"></a>Observaciones

## <a name="cache_freelistdeallocate"></a><a name="deallocate"></a>cache_freelist::deallocate

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

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
