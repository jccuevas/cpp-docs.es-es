---
title: Clase is_trivially_move_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 316ffdee4905ff8a35baef7137ff7f28a2846786
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958197"
---
# <a name="istriviallymoveconstructible-class"></a>Clase is_trivially_move_constructible

Comprueba si el tipo tiene un constructor de movimiento trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* es una clase que tiene un constructor de movimiento trivial, en caso contrario, es false.

Un constructor de movimiento para una clase *Ty* es trivial si:

se declara de forma implícita

sus tipos de parámetro son equivalentes a los de una declaración implícita

la clase *Ty* no tiene ninguna función virtual

la clase *Ty* tiene ninguna base virtual

la clase no tiene ningún miembro de datos no estáticos volátil

todas las bases directas de la clase *Ty* tienen constructores de movimiento trivial

las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de movimiento triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
