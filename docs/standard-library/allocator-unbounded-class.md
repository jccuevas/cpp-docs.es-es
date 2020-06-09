---
title: allocator_unbounded (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: ba4c8b774752b327f5a4ede84fa804888cfd31d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617384"
---
# <a name="allocator_unbounded-class"></a>allocator_unbounded (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo *Type* mediante una memoria caché de tipo [cache_freelist](cache-freelist-class.md) con una longitud administrada por [max_unbounded](max-unbounded-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Observaciones

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) pasa esta clase como parámetro *Name* en la siguiente instrucción:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Requisitos

**Encabezado:**\<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Consulte también

[\<allocators>](allocators-header.md)
