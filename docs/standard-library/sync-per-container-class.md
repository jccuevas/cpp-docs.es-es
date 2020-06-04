---
title: sync_per_container (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: 2c60911b5469cbf74944c9f63af44f2351790280
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376562"
---
# <a name="sync_per_container-class"></a>sync_per_container (Clase)

Describe un filtro de [sincronización](../standard-library/allocators-header.md) que proporciona un objeto de caché independiente para cada objeto de asignador.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Cache>
class sync_per_container
    : public Cache
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Memoria caché*|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funciones miembro

|Función de miembro|Descripción|
|-|-|
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="sync_per_containerequals"></a><a name="equals"></a>sync_per_container::igual es

Compara dos cachés para determinar si son iguales.

```cpp
bool equals(const sync_per_container<Cache>& Other) const;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Memoria caché*|El objeto de caché del filtro de sincronización.|
|*Otros*|El objeto de caché para comparar la igualdad.|

### <a name="return-value"></a>Valor devuelto

La función miembro siempre devuelve **false**.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[\<asignadores>](../standard-library/allocators-header.md)
