---
title: Clase is_nothrow_copy_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: 330c97cd945e161d2bf47deb377dd732bf53b3c9
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455978"
---
# <a name="isnothrowcopyassignable-class"></a>Clase is_nothrow_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia que el compilador sabe que no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true para un tipo *T* al que `is_nothrow_assignable<T&, const T&>` se hace referencia, donde contiene true; en caso contrario, contiene false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)\
[Clase is_nothrow_assignable](../standard-library/is-nothrow-assignable-class.md)
