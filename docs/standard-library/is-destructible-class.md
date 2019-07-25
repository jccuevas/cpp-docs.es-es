---
title: Clase is_destructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: 80592a6fca274533a798b2f5a2459d336ee2c301
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452734"
---
# <a name="isdestructible-class"></a>Clase is_destructible

Comprueba si el tipo se puede destruir.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es un tipo puede destruir; en caso contrario, contiene false. Los tipos que se pueden destruir son tipos de referencia, tipos de objetos y tipos en los que para algún tipo `U` igual a `remove_all_extents_t<T>` el operando no evaluado `std::declval<U&>.~U()` tiene un formato correcto. Otros tipos, incluidos los tipos incompletos, **void**y los tipos de función, no son tipos puede destruir.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
