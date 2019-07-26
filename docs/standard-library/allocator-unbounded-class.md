---
title: allocator_unbounded (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 38ecec3848808585ac0ed7cb1b076480a79f6d41
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448299"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo *Type* mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_unbounded](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Comentarios

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) pasa esta clase como parámetro *Name* en la siguiente instrucción:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
