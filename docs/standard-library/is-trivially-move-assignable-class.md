---
title: Clase is_trivially_move_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 324e4a1f1bd3528f09f21c5e485ac814038b7517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448380"
---
# <a name="istriviallymoveassignable-class"></a>Clase is_trivially_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un operador de asignación de movimiento trivial; en caso contrario, contiene false.

Un operador de asignación de movimiento para una clase *Ty* es trivial si:

se proporciona de forma implícita

la clase *Ty* no tiene ninguna función virtual

la clase *Ty* no tiene ninguna base virtual

las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación de movimiento triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
