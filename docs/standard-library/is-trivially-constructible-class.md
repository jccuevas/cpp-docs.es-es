---
title: Clase is_trivially_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_constructible
helpviewer_keywords:
- is_trivially_constructible
ms.assetid: 3fa918c1-e66f-4d0e-a11b-be1fb2c02e7b
ms.openlocfilehash: 6f177463b985d3e7b2f7ab7783f9c3db0dcd5722
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448014"
---
# <a name="istriviallyconstructible-class"></a>Clase is_trivially_constructible

Comprueba si un tipo se puede construir de forma trivial cuando se usan los tipos de argumento especificados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class... Args>
struct is_trivially_constructible;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

*Args*\
Los tipos de argumento que deben coincidir en un constructor de *T*.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* se construye de forma trivial mediante los tipos de argumento de *args*; en caso contrario, contiene false. El tipo *T* se construye de forma trivial si la definición `T t(std::declval<Args>()...);` de variable tiene el formato correcto y se sabe que no llama a ninguna operación no trivial. *T* y todos los tipos de *args* deben ser tipos completos, **void**o matrices de enlazados desconocidos.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
