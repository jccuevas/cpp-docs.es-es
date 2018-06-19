---
title: cache_suballoc (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28dc4e52e2f114600ad3a22697500ce9d8594113
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33850312"
---
# <a name="cachesuballoc-class"></a>cache_suballoc (Clase)

Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.

## <a name="syntax"></a>Sintaxis

```cpp
template <std::size_t Sz, size_t Nelts = 20>
class cache_suballoc
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`Sz`|El número de elementos de la matriz que se van a asignar.|

## <a name="remarks"></a>Comentarios

La clase de plantilla cache_suballoc almacena bloques de memoria desasignados en una lista libre con longitud ilimitada, mediante `freelist<sizeof(Type), max_unbounded>`, y subasigna bloques de memoria de un fragmento mayor asignado con `operator new` cuando la lista libre está vacía.

Cada fragmento contiene `Sz * Nelts` bytes de memoria utilizable y los datos que `operator new` y `operator delete` requieren. Nunca se liberarán los fragmentos asignados.

### <a name="constructors"></a>Constructores

|Constructor|Descripción|
|-|-|
|[cache_suballoc](#cache_suballoc)|Construye un objeto de tipo `cache_suballoc`.|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
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

|Parámetro|Descripción|
|---------------|-----------------|
|`count`|El número de elementos de la matriz que se van a asignar.|

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

|Parámetro|Descripción|
|---------------|-----------------|
|`ptr`|Un puntero al primer objeto que se va a desasignar del almacenamiento.|
|`count`|El número de objetos que se van a desasignar del almacenamiento.|

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
