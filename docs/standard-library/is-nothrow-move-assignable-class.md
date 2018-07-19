---
title: Clase is_nothrow_move_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_move_assignable
ms.assetid: 000baa02-cbba-49de-9870-af730033348e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 311f4f26b1f63c089c1771e36ac70060fab6b894
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33852128"
---
# <a name="isnothrowmoveassignable-class"></a>Clase is_nothrow_move_assignable

Comprueba si el tipo tiene un operador de asignación de movimiento **nothrow**.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_nothrow_move_assignable;
```

### <a name="parameters"></a>Parámetros

`Ty` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo `Ty` tiene un operador de asignación de movimiento nothrow; en caso contrario, contiene false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
