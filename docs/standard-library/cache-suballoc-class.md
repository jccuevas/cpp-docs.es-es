---
title: cache_suballoc (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
ms.openlocfilehash: aa0ceda69fc169593719c3a4f81d308bb6cde284
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449653"
---
# <a name="cachesuballoc-class"></a>cache_suballoc (Clase)

Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Sz*|El número de elementos de la matriz que se van a asignar.|

## <a name="remarks"></a>Comentarios

La clase de plantilla cache_suballoc almacena los bloques de memoria desasignados en una lista libre con una longitud `freelist<sizeof(Type), max_unbounded>`sin enlazar, y subasigna bloques de memoria de un fragmento más grande asignado con el **operador New** cuando la lista libre está vacía.

Cada fragmento contiene `Sz * Nelts` bytes de memoria utilizable y los datos que el **operador New** y el **operador Delete** requieren. Nunca se liberarán los fragmentos asignados.

### <a name="constructors"></a>Constructores

|Constructor|DESCRIPCIÓN|
|-|-|
|[cache_suballoc](#cache_suballoc)|Construye un objeto de tipo `cache_suballoc`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
|-|-|
|[allocate](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="allocate"></a>  cache_suballoc::allocate

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

## <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc

Construye un objeto de tipo `cache_suballoc`.

```cpp
cache_suballoc();
```

### <a name="remarks"></a>Comentarios

## <a name="deallocate"></a>  cache_suballoc::deallocate

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
