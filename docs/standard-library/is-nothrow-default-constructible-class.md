---
title: Clase is_nothrow_default_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
ms.openlocfilehash: 76b58800a454f42f6b5b6fcea23df161c37564b2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455929"
---
# <a name="isnothrowdefaultconstructible-class"></a>Clase is_nothrow_default_constructible

Comprueba si el tipo tiene un constructor predeterminado que no produce excepciones.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Ty>
struct is_nothrow_default_constructible;
```

### <a name="parameters"></a>Parámetros

*Ty*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *Ty* tiene un constructor predeterminado nothrow; en caso contrario, contiene false. Una instancia del predicado de tipo es equivalente a `is_nothrow_constructible<Ty>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
