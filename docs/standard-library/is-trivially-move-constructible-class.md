---
title: Clase is_trivially_move_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_move_constructible
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
ms.openlocfilehash: 279da956eaff21c39c6e5ca563f26989105f7e74
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448360"
---
# <a name="istriviallymoveconstructible-class"></a>Clase is_trivially_move_constructible

Comprueba si el tipo tiene un constructor de movimiento trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un constructor de movimiento trivial; en caso contrario, contiene false.

Un constructor de movimiento para una clase *Ty* es trivial si:

se declara de forma implícita

sus tipos de parámetro son equivalentes a los de una declaración implícita

la clase *Ty* no tiene ninguna función virtual

la clase *Ty* no tiene ninguna base virtual

la clase no tiene ningún miembro de datos no estáticos volátil

todas las bases directas de la clase *Ty* tienen constructores de movimiento triviales

las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de movimiento triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
