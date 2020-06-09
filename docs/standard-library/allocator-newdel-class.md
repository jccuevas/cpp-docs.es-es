---
title: allocator_newdel (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
ms.openlocfilehash: aa5012f6657b2676756d1d8023274a524b451df3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617461"
---
# <a name="allocator_newdel-class"></a>allocator_newdel (Clase)

Implementa un asignador que usa el **operador Delete** para desasignar un bloque de memoria y un **operador New** para asignar un bloque de memoria.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Observaciones

La macro [ALLOCATOR_DECL](allocators-functions.md#allocator_decl) pasa esta clase como parámetro *Name* en la siguiente instrucción:`ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Requisitos

**Encabezado:**\<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Consulte también

[\<allocators>](allocators-header.md)
