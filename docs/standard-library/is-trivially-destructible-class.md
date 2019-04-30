---
title: Clase is_trivially_destructible
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivially_destructible
helpviewer_keywords:
- is_trivially_destructible
ms.assetid: 3f7a787d-2448-40c5-ac51-a228318e02ce
ms.openlocfilehash: 61d626c308338595a64031a45908ab299ae1a957
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409777"
---
# <a name="istriviallydestructible-class"></a>Clase is_trivially_destructible

Comprueba si el tipo se puede destruir de forma trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_trivially_destructible;
```

### <a name="parameters"></a>Parámetros

*T*<br/>
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es un tipo puede destruir y el compilador sabe que el destructor no se usa ninguna operación no trivial. En caso contrario, es False.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)<br/>
