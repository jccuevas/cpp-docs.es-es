---
title: Clase is_trivially_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_assignable
helpviewer_keywords:
- is_trivially_assignable
ms.assetid: 1284a8f7-4093-426d-9c9a-dabb46f90d6d
ms.openlocfilehash: 11aed7fbe2540984d8ed69f88b2a95649e8fee70
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457492"
---
# <a name="istriviallyassignable-class"></a>Clase is_trivially_assignable

Comprueba si un valor de tipo `From` se puede asignar de forma trivial al tipo `To`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_trivially_assignable;
```

### <a name="parameters"></a>Parámetros

*Para*\
El tipo del objeto que recibe la asignación.

*De*\
El tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión `declval<To>() = declval<From>()` debe tener el formato correcto y el compilador debe saber que no requiere ninguna operación no trivial. Y deben ser tipos completos, void o matrices de enlazados desconocidos.  `From` `To`

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
