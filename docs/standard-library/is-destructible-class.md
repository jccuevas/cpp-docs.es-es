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
ms.openlocfilehash: bd23064123513281099fa14a690679fa046657fe
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44106633"
---
# <a name="isdestructible-class"></a>Clase is_destructible

Comprueba si el tipo se puede destruir.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_destructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* puede destruir tipo es, en caso contrario, es false. Los tipos que se pueden destruir son tipos de referencia, tipos de objetos y tipos en los que para algún tipo `U` igual a `remove_all_extents_t<T>` el operando no evaluado `std::declval<U&>.~U()` tiene un formato correcto. Otros tipos, incluidos los tipos incompletos, **void**y tipos de función, no se pueden destruir.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
