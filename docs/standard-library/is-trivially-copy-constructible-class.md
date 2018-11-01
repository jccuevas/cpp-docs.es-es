---
title: is_trivially_copy_constructible (Clase)
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
ms.openlocfilehash: aa6d6b19ae2bd5d6967c57db61c5697c0c6153e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630521"
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible (Clase)

Comprueba si el tipo tiene un constructor de copia trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_trivially_copy_constructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es una clase que tiene un constructor de copias triviales, en caso contrario, es false.

Un constructor de copias para una clase *T* es trivial si se está declarado implícitamente, la clase *T* no tiene funciones virtuales o bases virtuales, todas las bases directas de la clase *T* tiene constructores de copias triviales, las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de copias triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de copias triviales.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
