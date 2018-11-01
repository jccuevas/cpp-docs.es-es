---
title: allocator_unbounded (Clase)
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::allocator_unbounded
- allocators/stdext::allocators::allocator_unbounded
helpviewer_keywords:
- allocator_unbounded class
ms.assetid: facbaea1-b320-4d99-96da-039b2642f352
ms.openlocfilehash: 4e5bf54b386a3c3fe4e2604a78437275707acbfd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50586295"
---
# <a name="allocatorunbounded-class"></a>allocator_unbounded (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo *tipo* mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_unbounded](../standard-library/max-unbounded-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_unbounded;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Comentarios

El [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) macro pasa esta clase como el *nombre* parámetro en la siguiente instrucción: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_unbounded), SYNC_DEFAULT, allocator_unbounded);`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
