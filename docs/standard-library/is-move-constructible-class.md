---
title: Clase is_move_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_move_constructible
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
ms.openlocfilehash: 1b1e450338a123c51b80f40f2369207c8b987cd6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383638"
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
