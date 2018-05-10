---
title: sync_per_container (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af1db124d7fa73a9483d2c77f0a1e78349224023
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="syncpercontainer-class"></a>sync_per_container (Clase)

Describe un [filtro de sincronización](../standard-library/allocators-header.md) que proporciona un objeto de caché independiente para cada objeto de asignador.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Cache>
class sync_per_container
 : public Cache
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`Cache`|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|Descripción|
|-|-|
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="equals"></a>  sync_per_container::equals

Compara dos cachés para determinar si son iguales.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`Cache`|El objeto de caché del filtro de sincronización.|
|`Other`|El objeto de caché para comparar la igualdad.|

### <a name="return-value"></a>Valor devuelto

La función miembro siempre devuelve `false`.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
