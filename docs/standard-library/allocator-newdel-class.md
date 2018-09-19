---
title: allocator_newdel (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocators::allocator_newdel
- allocators/stdext::allocator_newdel
- stdext::allocators::allocator_newdel
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocators [C++], allocator_newdel
- stdext::allocator_newdel
ms.assetid: 62666cd2-3afe-49f7-9dd1-9bbbb154da98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dde45090a534fc8d5aff09ee12b1b4fe838d9492
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966281"
---
# <a name="allocatornewdel-class"></a>allocator_newdel (Clase)

Implementa un asignador que usa **operador delete** para desasignar una memoria de bloque y **operador new** para asignar un bloque de memoria.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class allocator_newdel;
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Type*|Tipo de elementos que asigna el asignador.|

## <a name="remarks"></a>Comentarios

El [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) macro pasa esta clase como el *nombre* parámetro en la siguiente instrucción: `ALLOCATOR_DECL(CACHE_FREELIST stdext::allocators::max_none), SYNC_DEFAULT, allocator_newdel);`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[\<allocators>](../standard-library/allocators-header.md)<br/>
