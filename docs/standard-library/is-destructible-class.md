---
title: Clase is_destructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_destructible
ms.assetid: 3bb9b718-1ad5-49ae-93cc-92b93b546b4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b2c9237c7f17217d28e489edef4ab65863b54b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964123"
---
# <a name="isdestructible-class"></a>Clase is_destructible

Comprueba si el tipo se puede destruir.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parámetros

*T* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* puede destruir tipo es, en caso contrario, es false. Los tipos que se pueden destruir son tipos de referencia, tipos de objetos y tipos en los que para algún tipo `U` igual a `remove_all_extents_t<T>` el operando no evaluado `std::declval<U&>.~U()` tiene un formato correcto. Otros tipos, incluidos los tipos incompletos, **void**y tipos de función, no se pueden destruir.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
