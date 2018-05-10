---
title: Clase is_nothrow_destructible | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_destructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_destructible
ms.assetid: 0bbd8a28-e312-4d72-bd28-aac027f974d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d8980119a3414159018102b8a0d1ad7fb0e8fe76
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="isnothrowdestructible-class"></a>Clase is_nothrow_destructible

Comprueba si el tipo se puede destruir y el compilador sabe que el destructor no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_nothrow_destructible;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true si el tipo `T` se puede destruir y el compilador sabe que el destructor no se inicia. En caso contrario, es False.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
