---
title: Clase is_nothrow_copy_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
ms.openlocfilehash: bb3aca47b61bdcc5b28eeedc1a6b4edefc303c4e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50583760"
---
# <a name="isnothrowcopyassignable-class"></a>Clase is_nothrow_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia que el compilador sabe que no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true para un tipo de referencia *T* donde `is_nothrow_assignable<T&, const T&>` es true; en caso contrario, es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable (Clase)](../standard-library/is-nothrow-assignable-class.md)<br/>
