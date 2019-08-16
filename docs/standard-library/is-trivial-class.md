---
title: Clase is_trivial
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_trivial
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
ms.openlocfilehash: 1d218848fd65ca68022e3e66df02201582626711
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457413"
---
# <a name="istrivial-class"></a>Clase is_trivial

Comprueba si el tipo es un tipo trivial.

## <a name="syntax"></a>Sintaxis

```cpp
template <class T>
struct is_trivial;
```

### <a name="parameters"></a>Parámetros

*H*\
Tipo que se va a consultar.

## <a name="remarks"></a>Comentarios

Una instancia del predicado de tipo contiene true si el tipo *T* es un tipo trivial; en caso contrario, contiene false. Los tipos triviales son tipos escalares, tipos de clase que se pueden copiar de forma trivial, matrices de estos tipos y versiones de tipo cv-qualified (const, volatile, const volatile) de estos tipos.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<type_traits>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[<type_traits>](../standard-library/type-traits.md)
