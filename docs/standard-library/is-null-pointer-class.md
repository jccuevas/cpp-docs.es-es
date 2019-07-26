---
title: Clase is_null_pointer
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_null_pointer
helpviewer_keywords:
- is_null_pointer
ms.assetid: f3b3601b-f162-4803-a6e9-dabf5c3876cc
ms.openlocfilehash: b306753146a51bde842b55e4f36d3c1afa82591d
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455843"
---
# <a name="isnullpointer-class"></a>Clase is_null_pointer

Comprueba si el tipo es std::nullptr_t.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_null_pointer;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el  tipo T `std::nullptr_t`es; en caso contrario, contiene false.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
