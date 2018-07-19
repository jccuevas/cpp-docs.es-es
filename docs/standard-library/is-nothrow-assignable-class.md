---
title: Clase is_nothrow_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_assignable
ms.assetid: aa3aca92-308b-4b1d-b3f3-c54216c48fe7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 424fcf5b960182326dc1192d8d60f168ead59d98
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965420"
---
# <a name="isnothrowassignable-class"></a>Clase is_nothrow_assignable

Comprueba si un valor de *desde* tipo puede asignarse a *a* se conoce el tipo y la asignación no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class To, class From>
struct is_nothrow_assignable;
```

### <a name="parameters"></a>Parámetros

*Para* el tipo del objeto que recibe la asignación.

*Desde* el tipo del objeto que proporciona el valor.

## <a name="remarks"></a>Comentarios

La expresión `declval<To>() = declval<From>()` debe tener el formato correcto y el compilador debe saber que no se inicia. Ambos *desde* y *a* deben ser tipos completos, **void**, o matrices de límite desconocido.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
