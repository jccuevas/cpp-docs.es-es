---
title: Clase is_trivially_move_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58bcd000f34941ec37141f9be4b4b3a56e0b9197
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallymoveconstructible-class"></a>Clase is_trivially_move_constructible

Comprueba si el tipo tiene un constructor de movimiento trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un constructor de movimiento trivial; en caso contrario, contiene false.

Un constructor de movimiento para una clase `Ty` es trivial si:

se declara de forma implícita

sus tipos de parámetro son equivalentes a los de una declaración implícita

la clase `Ty` no tiene ninguna función virtual

la clase `Ty` no tiene ninguna base virtual

la clase no tiene ningún miembro de datos no estáticos volátil

todas las bases directas de la clase `Ty` tienen constructores de movimiento trivial

las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de movimiento triviales

las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de movimiento triviales

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
