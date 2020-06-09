---
title: allocator_variable_size (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
ms.openlocfilehash: 4e4c5ab0167d49c9ee892f39f18892edd004c3f6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623701"
---
# <a name="allocator_variable_size-class"></a>allocator_variable_size (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo *Type* mediante una memoria caché de tipo [cache_freelist](cache-freelist-class.md) con una longitud administrada por [max_variable_size](max-variable-size-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Observaciones

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) pasa esta clase como parámetro *Name* en la siguiente instrucción:`ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>Requisitos

**Encabezado:**\<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Consulte también

[\<allocators>](allocators-header.md)
