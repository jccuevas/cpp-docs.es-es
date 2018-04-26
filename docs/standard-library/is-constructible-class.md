---
title: Clase is_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b030d50861a207828b406bd683f02089070755be
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="isconstructible-class"></a>clase is_constructible

Comprueba si un tipo se puede construir cuando se usan los tipos de argumento especificados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

`Args` Los tipos de argumentos para que coincida con un constructor de `T`.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `T` se puede construir mediante los tipos de argumento de `Args`. En caso contrario, es false. El tipo `T` se puede construir si la definición de variable `T t(std::declval<Args>()...);` tiene el formato correcto. Tanto `T` como todos los tipos de `Args` deben ser tipos completos, `void` o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
