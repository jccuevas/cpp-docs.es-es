---
title: Clase is_trivially_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 757a5eb526bc8d4294a64cbdc9645e72285162ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="istriviallyconstructible-class"></a>Clase is_trivially_constructible

Comprueba si un tipo se puede construir de forma trivial cuando se usan los tipos de argumento especificados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

`Args` Los tipos de argumentos para que coincida con un constructor de `T`.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `T` se puede construir de forma trivial mediante los tipos de argumento de `Args`. En caso contrario, es false. El tipo `T` se puede construir de forma trivial si la definición de variable `T t(std::declval<Args>()...);` tiene el formato correcto y se sabe que no llama a ninguna operación no trivial. Tanto `T` como todos los tipos de `Args` deben ser tipos completos, `void` o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
