---
title: Clase is_trivially_copy_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_assignable
helpviewer_keywords:
- is_trivially_copy_assignable
ms.assetid: 7410133e-f367-493f-92a7-e34e3ec5e879
ms.openlocfilehash: 831e7c5afdd39980876a8e8284a68fec2084a4e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630989"
---
# <a name="istriviallycopyassignable-class"></a>Clase is_trivially_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_copy_assignable;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es una clase que tiene un copia trivial operador de asignación, en caso contrario, es false.

Un constructor de asignación para una clase *T* es trivial si se proporciona implícitamente, la clase *T* no tiene ninguna función virtual, la clase *T* tiene ninguna base virtual, las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación triviales.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
