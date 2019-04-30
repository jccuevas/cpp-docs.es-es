---
title: Clase is_destructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_destructible
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
ms.openlocfilehash: 1036a3756a736ee3916ed9fca84aa935bb0ba2cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62336834"
---
# <a name="isdestructible-class"></a>Clase is_destructible

Comprueba si el tipo se puede destruir.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* puede destruir tipo es, en caso contrario, es false. Los tipos que se pueden destruir son tipos de referencia, tipos de objetos y tipos en los que para algún tipo `U` igual a `remove_all_extents_t<T>` el operando no evaluado `std::declval<U&>.~U()` tiene un formato correcto. Otros tipos, incluidos los tipos incompletos, **void**y tipos de función, no se pueden destruir.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
