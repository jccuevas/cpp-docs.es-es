---
title: Clase is_trivially_move_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1248c8efd06069863a9f78a94378fe7aed651011
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856090"
---
# <a name="istriviallymoveassignable-class"></a>Clase is_trivially_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un operador de asignación de movimiento trivial; en caso contrario, contiene false.

Un operador de asignación de movimiento para una clase `Ty` es trivial si:

se proporciona de forma implícita

la clase `Ty` no tiene ninguna función virtual

la clase `Ty` no tiene ninguna base virtual

las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación de movimiento triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
