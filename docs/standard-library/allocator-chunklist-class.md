---
title: allocator_chunklist (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
ms.openlocfilehash: c2342d068293714871b3f79675dd0d0b9db83448
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617546"
---
# <a name="allocator_chunklist-class"></a>allocator_chunklist (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos mediante una memoria caché de tipo [cache_chunklist](cache-chunklist-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Observaciones

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) pasa esta clase como parámetro *Name* en la siguiente instrucción:`ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Requisitos

**Encabezado:**\<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Consulte también

[\<allocators>](allocators-header.md)
