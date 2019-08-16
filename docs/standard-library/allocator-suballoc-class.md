---
title: allocator_suballoc (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
ms.openlocfilehash: 3e5b69ef3f47a173ef768283bbae4f6e3b5f5190
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458138"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo *Type* mediante una memoria caché de tipo [cache_suballoc](../standard-library/cache-suballoc-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Comentarios

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) pasa esta clase como parámetro *Name* en la siguiente instrucción:`ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)
