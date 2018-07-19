---
title: Clase is_trivially_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47fabb7120cc13eeca38bc9d06428f686fc9f1b9
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38955571"
---
# <a name="istriviallyassignable-class"></a>Clase is_trivially_assignable

Comprueba si un valor de tipo `From` se puede asignar de forma trivial al tipo `To`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parámetros

En el tipo del objeto que recibe la asignación.

Desde el tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión `declval<To>() = declval<From>()` debe tener el formato correcto y el compilador debe saber que no requiere ninguna operación no trivial. Ambos `From` y `To` deben ser tipos completos, **void**, o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
