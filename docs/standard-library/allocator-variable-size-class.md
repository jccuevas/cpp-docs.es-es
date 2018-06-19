---
title: allocator_variable_size (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_variable_size
- allocators/stdext::allocators::allocator_variable_size
- stdext::allocators::allocator_variable_size
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_variable_size
- stdext::allocators [C++], allocator_variable_size
ms.assetid: c3aa4105-ae45-4385-bbbe-9f23060478cb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 690be271cd7e9ad3eaf019f1feb67202c14a9e5c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33840607"
---
# <a name="allocatorvariablesize-class"></a>allocator_variable_size (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo `Type` mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_variable_size](../standard-library/max-variable-size-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_variable_size;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|`Type`|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Comentarios

La macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) pasa esta clase como el parámetro `name` de la instrucción siguiente: `ALLOCATOR_DECL(CACHE_FREELIST(stdext::allocators::max_variable_size), SYNC_DEFAULT, allocator_variable_size);`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
