---
title: Clase is_nothrow_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_assignable
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
ms.openlocfilehash: c59c3623f9c9548a7b7e59d0c56a2acd4d3883a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652470"
---
# <a name="isnothrowassignable-class"></a>Clase is_nothrow_assignable

Comprueba si un valor de *desde* tipo puede asignarse a *a* se conoce el tipo y la asignación no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Parámetros

*En*<br/>
El tipo del objeto que recibe la asignación.

*From*<br/>
El tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión `declval<To>() = declval<From>()` debe tener el formato correcto y el compilador debe saber que no se inicia. Ambos *desde* y *a* deben ser tipos completos, **void**, o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
