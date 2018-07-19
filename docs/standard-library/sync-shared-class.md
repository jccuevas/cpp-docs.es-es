---
title: sync_shared (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_shared
- stdext::sync_shared [C++], allocate
- stdext::sync_shared [C++], deallocate
- stdext::sync_shared [C++], equals
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fb9b61ec4d2abc6ae73b2ebed7571398857d517
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963464"
---
# <a name="syncshared-class"></a>sync_shared (Clase)

Describe un [filtro de sincronización](../standard-library/allocators-header.md) que usa una exclusión mutua para controlar el acceso a un objeto de caché compartido por todos los asignadores.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Cache>
class sync_shared
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Caché*|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[allocate](#allocate)|Asigna un bloque de memoria.|
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="allocate"></a>  sync_shared::allocate

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

### <a name="remarks"></a>Comentarios

La función miembro bloquea la exclusión mutua, llama a `cache.allocate(count)`, desbloquea la exclusión mutua y devuelve el resultado de la llamada anterior a `cache.allocate(count)`. `cache` representa el objeto de caché actual.

## <a name="deallocate"></a>  sync_shared::deallocate

Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.

```cpp
void deallocate(void* ptr, std::size_t count);
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*ptr*|Un puntero al primer objeto que se va a desasignar del almacenamiento.|
|*count*|El número de objetos que se van a desasignar del almacenamiento.|

### <a name="remarks"></a>Comentarios

Esta función miembro bloquea la exclusión mutua, llama a `cache.deallocate(ptr, count)`, donde `cache` representa el objeto de caché y, después, desbloquea la exclusión mutua.

## <a name="equals"></a>  sync_shared::equals

Compara dos cachés para determinar si son iguales.

```cpp
bool equals(const sync_shared<Cache>& Other) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Caché*|El tipo de caché asociado al filtro de sincronización.|
|*Otros problemas*|La caché para comparar la igualdad.|

### <a name="return-value"></a>Valor devuelto

**True** si el resultado de `cache.equals(Other.cache)`, donde `cache` representa el objeto de caché, es **true**; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
