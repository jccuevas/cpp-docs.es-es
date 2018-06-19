---
title: Clase is_nothrow_copy_assignable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_copy_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_copy_assignable
ms.assetid: baa8abd6-4f53-489f-abba-8d5d5c53bbbc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6c5c5bdc1e944483071f0f1dcd53c3bc93eb6ed3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842942"
---
# <a name="isnothrowcopyassignable-class"></a>Clase is_nothrow_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia que el compilador sabe que no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parámetros

`T` El tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo es true para un tipo de referencia `T` si `is_nothrow_assignable<T&, const T&>` es true; en caso contrario, es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable (Clase)](../standard-library/is-nothrow-assignable-class.md)<br/>
