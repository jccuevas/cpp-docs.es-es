---
title: sync_per_container (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
ms.openlocfilehash: 378451ac2643d62271fd9e7fa44706a84ee8bb83
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450288"
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

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Caché*|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|

### <a name="member-functions"></a>Funciones miembro

|Función miembro|DESCRIPCIÓN|
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

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Caché*|El objeto de caché del filtro de sincronización.|
|*Otros problemas*|El objeto de caché para comparar la igualdad.|

### <a name="return-value"></a>Valor devuelto

La función miembro siempre devuelve **false**.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
