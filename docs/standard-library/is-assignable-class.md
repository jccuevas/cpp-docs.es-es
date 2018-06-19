---
title: Clase is_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_assignable
ms.assetid: 53444287-c8be-4ad2-9487-a85c066a4f84
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd8b757ab46d462bd5d6a596f7dbbfdd18061a8d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843004"
---
# <a name="isassignable-class"></a>Clase is_assignable

Comprueba si un valor de tipo `From` se puede asignar a un tipo `To`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_assignable;
```

### <a name="parameters"></a>Parámetros

Para el tipo del objeto que recibe la asignación.

Desde el tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión no evaluada `declval<To>() = declval<From>()` debe tener un formato correcto. Tanto `From` como `To` deben ser tipos completos, `void` o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
