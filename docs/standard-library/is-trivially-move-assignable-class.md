---
title: Clase is_trivially_move_assignable
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_assignable
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
ms.openlocfilehash: 4b349d328da995105a6217f4ab597da5d7eafc38
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689489"
---
# <a name="is_trivially_move_assignable-class"></a>Clase is_trivially_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parámetros

@No__t_1 *Ty*
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un operador de asignación de movimiento trivial; en caso contrario, contiene false.

Un operador de asignación de movimiento para una clase *Ty* es trivial si:

- se proporciona de forma implícita
- la clase *Ty* no tiene ninguna función virtual
- la clase *Ty* no tiene ninguna base virtual
- las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación de movimiento triviales
- las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación de movimiento triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
