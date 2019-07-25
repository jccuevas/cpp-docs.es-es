---
title: clase is_constructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_constructible
helpviewer_keywords:
- is_constructible
ms.assetid: 7cdec5ff-73cf-4f78-a9db-ced2e9c0fd7f
ms.openlocfilehash: dc0596ac7a3fc2bcbcbe49f5fa4b20a971e5e445
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452859"
---
# <a name="isconstructible-class"></a>clase is_constructible

Comprueba si un tipo se puede construir cuando se usan los tipos de argumento especificados.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class... Args>
struct is_constructible;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

*Args*\
Los tipos de argumento que deben coincidir en un constructor de *T*.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* se construye mediante el uso de los tipos de argumento en *args*; en caso contrario, contiene false. El tipo *T* se construye si la definición `T t(std::declval<Args>()...);` de la variable tiene el formato correcto. *T* y todos los tipos de *args* deben ser tipos completos, **void**o matrices de enlazados desconocidos.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
