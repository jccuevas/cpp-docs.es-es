---
title: Clase is_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d5666aca2d6a855b64af26d38a1ae834fecec5d6
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958470"
---
# <a name="isassignable-class"></a>Clase is_assignable

Comprueba si un valor de tipo `From` se puede asignar a un tipo `To`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parámetros

En el tipo del objeto que recibe la asignación.

Desde el tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión no evaluada `declval<To>() = declval<From>()` debe tener un formato correcto. Ambos `From` y `To` deben ser tipos completos, **void**, o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
