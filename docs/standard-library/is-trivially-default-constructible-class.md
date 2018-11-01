---
title: is_trivially_default_constructible (clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_default_constructible
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
ms.openlocfilehash: b35458ca280285eb699c9b12b15b705660299ef2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563675"
---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible (clase)

Comprueba si el tipo tiene un constructor predeterminado trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_default_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un constructor trivial; en caso contrario, es false.

Un constructor predeterminado para una clase *Ty* es trivial si:

- es un constructor predeterminado declarado implícitamente

- la clase *Ty* no tiene ninguna función virtual

- la clase *Ty* tiene ninguna base virtual

- todas las bases directas de la clase *Ty* tienen constructores triviales

- las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores triviales

- las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
