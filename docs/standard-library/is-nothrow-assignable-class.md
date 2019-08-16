---
title: Clase is_nothrow_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: 9ee8b5f97c92b6eb378db40f93696e5e6c554205
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456022"
---
# <a name="isnothrowassignable-class"></a>Clase is_nothrow_assignable

Comprueba si un valor de *tipo de* tipo puede asignarse *al tipo y* se sabe que la asignación no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Parámetros

*Para*\
El tipo del objeto que recibe la asignación.

*De*\
El tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión `declval<To>() = declval<From>()` debe tener el formato correcto y el compilador debe saber que no se inicia. Tanto *desde* como *hasta* deben ser tipos completos, **void**o matrices de enlazados desconocidos.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
