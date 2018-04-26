---
title: underlying_type (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- type_traits/std::underlying_type
dev_langs:
- C++
helpviewer_keywords:
- underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52bf41cdcb40c88f32adc6d0384bea60f5997286
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="underlyingtype-class"></a>underlying_type (Clase)

Genera el tipo entero subyacente para un tipo de enumeración.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct underlying_type;
```

### <a name="parameters"></a>Parámetros

`T` Tipo que se va a modificar.

## <a name="remarks"></a>Comentarios

La definición de tipo miembro `type` de la clase de plantilla nombra el tipo entero subyacente de `T`, cuando `T` es un tipo de enumeración, de lo contrario, no hay ninguna definición de tipo miembro `type`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
