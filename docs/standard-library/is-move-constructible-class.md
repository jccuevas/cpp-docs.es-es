---
title: is_move_constructible (Clase)
ms.date: 10/24/2019
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 9585a932a34a24769201aaa379525a9b4c181e41
ms.sourcegitcommit: 33a898bf976c65f998b4e88a84765a0cef4193a8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920088"
---
# <a name="is_move_constructible-class"></a>is_move_constructible (Clase)

Comprueba si el tipo se puede construir mediante una operación de movimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parámetros

*T* \
Tipo que se va a evaluar.

## <a name="remarks"></a>Comentarios

Predicado de tipo que se evalúa como **true** si el tipo *T* se puede construir mediante una operación de movimiento. Este predicado es equivalente a `is_constructible<T, T&&>`. Un tipo *T* que no tiene un constructor de movimiento, pero que tiene un constructor de copias que acepta un argumento `const T&`, cumple `std::is_move_constructible`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
