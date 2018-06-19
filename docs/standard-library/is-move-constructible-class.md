---
title: Clase is_move_constructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_move_constructible
ms.assetid: becdf076-7419-488d-a335-78adf2478b9b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d87eac720b205560993a7d6995be8a8fe6ad6194
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843527"
---
# <a name="ismoveconstructible-class"></a>Clase is_move_constructible

Comprueba si el tipo tiene un constructor de movimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parámetros

El tipo de T que se debe evaluar

## <a name="remarks"></a>Comentarios

Predicado de tipo que da como resultado True si el tipo `T` se puede construir mediante una operación de movimiento. Este predicado es equivalente a `is_constructible<T, T&&>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
