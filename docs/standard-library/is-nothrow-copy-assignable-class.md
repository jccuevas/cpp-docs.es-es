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
ms.openlocfilehash: e540d6fe4c00772af01b187d24efae18fd62357f
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38957563"
---
# <a name="isnothrowcopyassignable-class"></a>Clase is_nothrow_copy_assignable

Comprueba si el tipo tiene un operador de asignación de copia que el compilador sabe que no se inicia.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_nothrow_copy_assignable;
```

### <a name="parameters"></a>Parámetros

*T* el tipo de consulta.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true para un tipo de referencia *T* donde `is_nothrow_assignable<T&, const T&>` es true; en caso contrario, es false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_nothrow_assignable (Clase)](../standard-library/is-nothrow-assignable-class.md)<br/>
