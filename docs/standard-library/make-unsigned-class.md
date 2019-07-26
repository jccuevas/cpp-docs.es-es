---
title: make_unsigned (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::make_unsigned
helpviewer_keywords:
- make_unsigned class
- make_unsigned
ms.assetid: 7a6a3c4f-1a4c-47e8-9ee2-ac1f7b669353
ms.openlocfilehash: 4c0224bd5fd7dc8c6589ae474bb9acb9a8f09cf6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456322"
---
# <a name="makeunsigned-class"></a>make_unsigned (Clase)

Hace que el tipo o el tipo sin signo más pequeño sea igual o superior en tamaño al tipo.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct make_unsigned;

template <class T>
using make_unsigned_t = typename make_unsigned<T>::type;
```

### <a name="parameters"></a>Parámetros

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|*T*|Tipo que se va a modificar.|

## <a name="remarks"></a>Comentarios

Una instancia del modificador de tipo contiene un tipo modificado que es *T* si `is_unsigned<T>` es true. En caso contrario, es el tipo con signo menor `ST` para el que `sizeof (T) <= sizeof (ST)`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
