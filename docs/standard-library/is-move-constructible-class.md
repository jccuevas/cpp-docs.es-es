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
ms.openlocfilehash: 6f9c0b381cfbf32327eef4b29a9dbe23f1d991f1
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108777"
---
# <a name="ismoveconstructible-class"></a>Clase is_move_constructible

Comprueba si el tipo tiene un constructor de movimiento.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_move_constructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo que se debe evaluar

## <a name="remarks"></a>Comentarios

Un predicado de tipo que se evalúa como true si el tipo *T* puede crearse mediante el uso de una operación de movimiento. Este predicado es equivalente a `is_constructible<T, T&&>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
