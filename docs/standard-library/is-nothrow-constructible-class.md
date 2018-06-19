---
title: Clase is_nothrow_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_constructible
ms.assetid: 8be3f927-283e-4d67-95a5-8bf5dc4e7a3d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 112da495673517f86a00437672ccc52429fbd251
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842747"
---
# <a name="isnothrowconstructible-class"></a>Clase is_nothrow_constructible

Comprueba si un tipo se puede construir y se sabe que no se inicia cuando se usan los tipos de argumento especificados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class... Args>
struct is_nothrow_constructible;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

`Args` Los tipos de argumentos para que coincida con un constructor de `T`.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `T` se puede construir mediante los tipos de argumento de `Args` y el compilador sabe que el constructor no se inicia. En caso contrario, es false. El tipo `T` se puede construir si la definición de variable `T t(std::declval<Args>()...);` tiene el formato correcto. Tanto `T` como todos los tipos de `Args` deben ser tipos completos, `void` o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
