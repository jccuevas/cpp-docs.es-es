---
title: Clase is_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_assignable
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
ms.openlocfilehash: 33b0ce6112119c935ff70e5d619b284acc6ee8c2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456665"
---
# <a name="isassignable-class"></a>Clase is_assignable

Comprueba si un valor de tipo `From` se puede asignar a un tipo `To`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parámetros

*Para*\
El tipo del objeto que recibe la asignación.

*De*\
El tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión no evaluada `declval<To>() = declval<From>()` debe tener un formato correcto. Y deben ser tipos completos, void o matrices de enlazados desconocidos.  `From` `To`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
