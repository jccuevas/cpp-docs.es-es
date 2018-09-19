---
title: allocator_suballoc (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocators::allocator_suballoc
- allocators/stdext::allocator_suballoc
dev_langs:
- C++
helpviewer_keywords:
- allocator_suballoc class
ms.assetid: 50c6a5c0-d00d-4276-9285-d908fd4f6483
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6238aeada530a8fc33fc98b79cba969353796ae
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953093"
---
# <a name="allocatorsuballoc-class"></a>allocator_suballoc (Clase)

Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo *tipo* mediante una memoria caché de tipo [cache_suballoc](../standard-library/cache-suballoc-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_suballoc;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Comentarios

El [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) macro pasa esta clase como el *nombre* parámetro en la siguiente instrucción: `ALLOCATOR_DECL(CACHE_SUBALLOC, SYNC_DEFAULT, allocator_suballoc);`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
