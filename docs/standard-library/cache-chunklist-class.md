---
title: cache_chunklist (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
ms.openlocfilehash: d0dd6176a34bd625069511106c491225d1467d08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366757"
---
# <a name="cache_chunklist-class"></a>cache_chunklist (Clase)

Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, std::size_t Nelts = 20>
class cache_chunklist
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Sz*|El número de elementos de la matriz que se van a asignar.|

## <a name="remarks"></a>Observaciones

Esta plantilla de clase utiliza **el operador new** para asignar fragmentos de memoria sin procesar, subasignando bloques para asignar almacenamiento para un bloque de memoria cuando sea necesario; almacena bloques de memoria desasignados en una lista libre independiente para cada fragmento y utiliza **operator delete** para desasignar un fragmento cuando ninguno de sus bloques de memoria está en uso.

Cada bloque de memoria contiene *sz* bytes de memoria utilizable y un puntero al fragmento al que pertenece. Cada fragmento `Nelts` contiene bloques de memoria, tres punteros, un int y los datos que requieren **el operador new** y el operador **delete.**

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[cache_chunklist](#cache_chunklist)|Construye un objeto de tipo `cache_chunklist`.|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[Asignar](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="cache_chunklistallocate"></a><a name="allocate"></a>cache_chunklist::asignar

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

## <a name="cache_chunklistcache_chunklist"></a><a name="cache_chunklist"></a>cache_chunklist::cache_chunklist

Construye un objeto de tipo `cache_chunklist`.

```cpp
cache_chunklist();
```

### <a name="remarks"></a>Observaciones

## <a name="cache_chunklistdeallocate"></a><a name="deallocate"></a>cache_chunklist::deallocate

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
