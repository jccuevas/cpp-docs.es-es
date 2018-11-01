---
title: Clase is_move_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 1b1e450338a123c51b80f40f2369207c8b987cd6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509002"
---
# <a name="ismoveconstructible-class"></a>Clase is_move_constructible

Comprueba si el tipo tiene un constructor de movimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo que se debe evaluar

## <a name="remarks"></a>Comentarios

Un predicado de tipo que se evalúa como true si el tipo *T* puede crearse mediante el uso de una operación de movimiento. Este predicado es equivalente a `is_constructible<T, T&&>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
